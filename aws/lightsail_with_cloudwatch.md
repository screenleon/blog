# Lightsail with CloudWatch

**Author**: Lien Chen  **Date**: 2025-06-12

## 目錄

1. 背景與需求  
2. IAM 憑證：Lightsail 必走 OnPrem 模式  
3. CloudWatch Agent 設定檔範例  
4. 權限陷阱：x 才是目錄「通行證」  
5. 如果懶得調權限→直接用 root  
6. 驗證流程與常見錯誤  
7. 參考文件

---

## 背景與需求

- **平台**：AWS Lightsail (基底其實就是 EC2)  
- **目標**：把應用程式 log 送到 `YOUR_LOG_GROUP`，並保留 30 天  
- **限制**：Lightsail 没有 Instance Profile，**不能** 用 EC2 Role 簽名

---

## IAM 憑證：Lightsail 必走 OnPrem 模式

- **建 IAM 使用者**  
  - 至少掛 **CloudWatchAgentServerPolicy**，含 **(logs:CreateLogGroup/PutLogEvents)** 權限

- **建憑證檔** `/home/cwagent/.aws/credentials`  
  - 使用 `aws configure --profile YOUR_PROFILE` 設定客製化 profile 名稱（預設為 default）

- **OnPrem 啟動**  
    - `amazon-cloudwatch-agent-ctl -a fetch-config -m onPrem ...` 中的 `-m onPrem` **必須** 與設定檔 `"mode": "OnPrem"` 對應

- **指定 credentials 檔位置**  
  - 在設定檔最外層加入
  ```
      “credentials”: {  
          “shared_credential_file”: “/home/cwagent/.aws/credentials”,  
          “profile”: “YOUR_PROFILE”  
      }
  ```

---

## CloudWatch Agent 設定檔範例（最小可行）

<details>
  <summary>📄 amazon-cloudwatch-agent.json</summary>

    {
      "agent": {
        "metrics_collection_interval": 60,
        "run_as_user": "cwagent"
      },
      "credentials": {
        "shared_credential_file": "/home/cwagent/.aws/credentials",
        "profile": "YOUR_PROFILE"
      },
      "logs": {
        "force_flush_interval": 5,
        "logs_collected": {
          "files": {
            "collect_list": [
              {
                "file_path": "YOUR_LOG_PATH",
                "from_beginning": true,
                "log_group_name": "YOUR_LOG_GROUP",
                "log_stream_name": "{hostname}",
                "retention_in_days": 30,
                "timezone": "LOCAL"
              }
            ]
          }
        }
      }
    }

</details>

---

## 權限陷阱：x 才是目錄「通行證」

CloudWatch Agent 以 `cwagent` 身分讀檔；要能 `stat()` 檔案，**每一級目錄**都必須有 execute (x) 權限，否則看不到檔案。

    # 給最小必要權限：others 拿到 x
    sudo chmod 711 /home/ec2-user
    sudo setfacl -m u:cwagent:rx /home/ec2-user
    sudo setfacl -m u:cwagent:rx /home/ec2-user/tyoho/logs/backend

*或*

    # 直接把整棵路徑交給 cwagent
    sudo chown -R cwagent:cwagent /home/ec2-user/tyoho/logs/backend

> 如果權限不足，agent log 會一直刷  
> “Stat file … permission denied”  
> 此时可删掉 state 目录下所有文件重试：  
> `/opt/aws/amazon-cloudwatch-agent/logs/state/*`

---

## 如果懶得調權限→直接用 root

- 在設定檔 `agent` 區塊把  
    run_as_user: "cwagent"  
  改成  
    run_as_user: "root"  
  或者干脆**刪掉**這行（预设即 root）。  
- **注意**：root 可讀全系统，务必确认 `collect_list` 只包含必要檔案。

---

## 驗證流程與常見錯誤

    # 1. 停服务
    sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a stop

    # 2. 重载設定
    sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
         -a fetch-config -m onPrem \
         -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json -s

    # 3. 加一行測試字
    echo "$(date) test log line" >> /home/ec2-user/YOUR_LOG_PATH

    # 4. 监看 agent 日志
    sudo tail -f /opt/aws/amazon-cloudwatch-agent/logs/amazon-cloudwatch-agent.log

| 日誌訊息                      | 意義                             | 解法                            |
|-------------------------------|----------------------------------|---------------------------------|
| Successfully published N events | 完全 OK                          | —                               |
| permission denied             | 目錄或檔案缺少 x / r              | § 4 調整目錄 / 檔案權限         |
| UnrecognizedClientException   | IAM Key 錯誤或失效               | 重建 IAM Key，检查 region 設定 |
| ec2metadata is not available  | -m onPrem 與 `"mode"` 設定不一致 | 同步指令與設定檔模式           |

---

## 參考文件

- AWS「Common scenarios with the CloudWatch agent」– run_as_user 与 credentials 說明  
- CloudWatch Agent Configuration File 详解 – run_as_user 屬性  
- 安裝 On-Prem Agent 官方文件  
- IAM Role/User for CloudWatch Agent  
- Linux 目錄 x 權限概念  
- Agent state file 行為說明  
- GitHub issue：permission denied thread  
- Log group & stream retention 指南  
- On-Prem fetch-config 範例 (CN docs)

---

