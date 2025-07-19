# Velociraptor Agent Setup Guide (Windows)

This document describes how to install and configure the Velociraptor agent on a Windows 10 virtual machine.

---

## Prerequisites

- Windows 10 (or later) VM with internet access  
- Administrator privileges on the Windows VM  
- Velociraptor server already set up and running (see `velociraptor-server.md`)  

---

## Step 1: Download Velociraptor Windows Client

1. Go to the [Velociraptor releases page](https://github.com/Velocidex/velociraptor/releases).  
2. Download the latest **Windows client** zip file (e.g., `velociraptor-v0.9.3-win64.zip`).

---

## Step 2: Extract the Files

- Extract the downloaded zip to a folder, for example:  
  `C:\velociraptor`

---

## Step 3: Generate Agent Configuration on the Server

- On your Velociraptor server web UI, create a new client configuration profile if not done already.  
- Download the generated `client.config.yaml` configuration file and transfer it to your Windows VM (e.g., place it in `C:\velociraptor`).

---

## Step 4: Run the Velociraptor Agent

1. Open **PowerShell as Administrator**.  
2. Navigate to the Velociraptor folder:  
   ```powershell
   cd C:\velociraptor
   ```
3. Run the agent with the config file:  
   ```powershell
   .\velociraptor.exe -c client.config.yaml client
   ```
4. The agent will start and connect to the Velociraptor server.

---

## Step 5: Verify Connection

- On the Velociraptor server web UI, check if the new client shows up in the clients list.  
- You can start running hunts and queries targeting this agent.

---

## Step 6: (Optional) Run Agent as a Windows Service

- To have the agent run continuously in the background, set it up as a Windows service.  
- Use [NSSM (Non-Sucking Service Manager)](https://nssm.cc/) or create a scheduled task to run the agent at startup.

---

## Troubleshooting

- Make sure firewall rules allow the agent to communicate with the server.  
- Check agent logs in the Velociraptor folder for errors.

---

## Next Steps

- Perform attack simulations on the Windows VM and detect them using Velociraptor.  

---

Useful Commands Summary
Command	Description
service install	Install Velociraptor as service
Start-Service velociraptor	Start Velociraptor service
Stop-Service velociraptor	Stop Velociraptor service
Get-Service velociraptor	Check service status
.\velociraptor.exe -c agent.config.yaml client --verbose	Run agent interactively with verbose logging



**End of Velociraptor Agent Setup Guide**
