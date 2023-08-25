# Reload environment

An easy script to reload the environment to avoid reopen a new session terminal.

### Powershell
```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User") 
```
---

### Bash
```bash
source ~/.bashrc
```

```bash
source YOUR_FILE
```
---

