# WSL2 Port Forwarding Issue Resolved by Restarting IP Helper Service
================================

**Author**: Lien Chen  **Date**: 2025-05-16

While setting up my WSL2 environment to allow access to a development server from other devices on the same local network, I encountered an unexpected issue. I had configured port forwarding using netsh interface portproxy and ensured that the necessary firewall rules were in place. This setup had been working flawlessly for several days.

However, one day, external devices could no longer connect to the server hosted within WSL2. I verified that the port forwarding rules were still present by running netsh interface portproxy show all, and confirmed that the WSL2 instance was running and the server was active. Despite this, connections from other devices on the LAN were being refused.

After extensive troubleshooting, I discovered that restarting the Windows IP Helper service (iphlpsvc) resolved the issue. Here's how you can do this:

1. Press Win + R, type services.msc, and press Enter.
2. In the Services window, scroll down and locate IP Helper.
3. Right-click on IP Helper and select Restart.

You also can use script to restart the Windows IP Helper service.
```powershell=
# Restart the IP Helper service
Restart-Service -Name iphlpsvc -Force
```

Once the service was restarted, external devices were again able to connect to the WSL2-hosted server without any issues.