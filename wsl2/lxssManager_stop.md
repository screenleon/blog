# LxssManager Stopping with No Response
================================

**Author**: Lien Chen  **Date**: 2021-12-15

* Sometime, shutdown the WSL2 will face that LxssManager incomplete end. 
* To force quit process, I use command at below to get the LxssManager thread.

```powershell
tasklist /svc | Select-String "LxssManager"
```

* Finally use Process Hacker to stop the process.


[Get process ID](https://stackoverflow.com/questions/26331183/how-to-get-process-id-by-its-service-name-with-a-script-to-variable)
