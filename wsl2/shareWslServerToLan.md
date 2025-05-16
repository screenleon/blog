# ShareWslServerToLan 使用說明
================================

**Author**: Lien Chen  **Date**: 2025-03-19

此文檔說明如何將 WSL (Windows Subsystem for Linux) 中的伺服器共享到局域網 (LAN)，並透過 Windows 的 `netsh interface portproxy` 指令進行轉發設定。

## 一、啟動 WSL 伺服器

在 WSL 中，設定 `HOST=0.0.0.0` 可以讓伺服器監聽所有網路介面，然後執行 `npm start` 啟動應用。這樣一來，伺服器就可以接受來自其他機器的連線請求。

```bash
HOST=0.0.0.0 npm start
```

## 二、設定 Windows 端的 Port Proxy

由於 WSL 與 Windows 本身之間可能有網路隔離，為了讓局域網內的其他設備可以存取 WSL 中運行的伺服器，需要利用 Windows 的 `netsh interface portproxy` 指令進行轉發。以下為相關指令及用途：

### 1. 新增轉發規則

使用 `netsh interface portproxy add v4tov4` 指令，將指定的 LAN IP 與埠轉發到 WSL 中運行的伺服器。

```powershell=
$wslIp = wsl hostname -I
netsh interface portproxy add v4tov4 listenport=443 listenaddress=0.0.0.0 connectport=443 connectaddress=$wslIp
```

- **listenaddress:** 指定 Windows 上用於監聽的 IP (LAN IP)。
- **listenport:** 指定 Windows 上用於監聽的埠 (例如 3000)。
- **connectaddress:** 指向 WSL 中伺服器所監聽的 IP 地址 (根據實際配置可能與 listenaddress 相同或不同)。
- **connectport:** WSL 中伺服器所監聽的埠號 (例如 3000)。

### 2. 檢查所有轉發規則

可使用以下指令來檢查目前所有設定的 portproxy 規則，確認設定是否正確。

```bash
netsh interface portproxy show all
```

### 3. 刪除轉發規則

若需要移除先前新增的轉發規則，可以使用以下指令來刪除：

```bash
netsh interface portproxy delete v4tov4 listenaddress=192.168.X.X listenport=3000
```

此指令會根據指定的 `listenaddress` 與 `listenport` 來刪除對應的轉發規則。

## 三、注意事項

- **IP 位址設定：**  
  請確認 `192.168.X.X` 的 IP 地址已正確設定，依據你的局域網環境可能需要修改為實際的 LAN IP。

- **防火牆設定：**  
  在某些情況下，Windows 防火牆可能會阻擋相關連線，請確保已允許相關埠的連線。

- **WSL 與 Windows 的網路配置：**  
  若出現連線問題，請檢查 WSL 與 Windows 之間的網路配置，確保轉發規則正確無誤。

以上就是將 WSL 伺服器共享至 LAN 的完整流程與說明，可依據實際需求進行調整與擴充。
