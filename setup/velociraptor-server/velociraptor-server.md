
# Velociraptor Server Setup Guide

## Overview

Velociraptor is an open-source endpoint visibility and monitoring tool designed for incident response and threat hunting. This guide explains how to install and configure the Velociraptor server on an Ubuntu Linux VM.

---

## Prerequisites

- Ubuntu 20.04 or later VM
- Internet access for downloading Velociraptor binaries
- Basic Linux command-line knowledge
- Administrative (sudo) access on the Ubuntu VM

---

## Step 1: Download Velociraptor Server Binary

1. Visit the [Velociraptor GitHub Releases](https://github.com/Velocidex/velociraptor/releases) page and locate the latest stable release.

2. Download the Linux AMD64 binary. For example, version `v0.74.5`:

```bash
cd ~/Downloads
curl -LO https://github.com/Velocidex/velociraptor/releases/download/v0.74.5/velociraptor-v0.74.5-linux-amd64
```

---

## Step 2: Make the Binary Executable and Move to PATH

```bash
chmod +x velociraptor-v0.74.5-linux-amd64
sudo mv velociraptor-v0.74.5-linux-amd64 /usr/local/bin/velociraptor
```

Now you can run Velociraptor using the command `velociraptor` from any directory.

---

## Step 3: Generate Server Configuration

Run the interactive configuration wizard to create the server configuration file:

```bash
sudo velociraptor config generate -i
```

You will be prompted to configure:

- Deployment type (choose **Self Signed SSL** for lab)
- Server OS (choose **Linux**)
- Frontend bind address (use `0.0.0.0` to accept connections from agents)
- Frontend port (default `8000`)
- Public hostname (use your Ubuntu VM IP address)
- GUI bind address (default `127.0.0.1` or `0.0.0.0` to access GUI remotely)
- GUI port (default `8889`)
- Admin username and password

Finally, save the configuration file, e.g., `/home/youruser/Downloads/server.config.yaml`.

---

## Step 4: Start the Velociraptor Server Frontend

Start the server with the configuration file:

```bash
sudo velociraptor --config /home/youruser/Downloads/server.config.yaml frontend
```

You should see output indicating the frontend and admin GUI are listening, e.g.:

```
Frontend listening on https://0.0.0.0:8000/
Admin GUI on https://127.0.0.1:8889/
```

---

## Step 5: Access the Velociraptor Web GUI

Open a browser and navigate to:

```
http://<your-ubuntu-vm-ip>:8000
```

Log in with the admin credentials you set during configuration.

---

## Step 6: Generate Windows Agent Configuration (For Later Use)

Generate a client configuration file for Windows agents:

```bash
sudo velociraptor --config /home/youruser/Downloads/server.config.yaml config client > /home/youruser/Downloads/agent.config.yaml
```

This file is used to configure the Windows agent to connect to the server.

---

## Additional Notes

- You can stop the server by pressing `Ctrl + C` in the terminal where Velociraptor is running.
- Consider setting up Velociraptor as a systemd service for persistent operation.
- Always keep your Velociraptor binaries up to date for latest features and security fixes.

---

## References

- [Velociraptor Official Documentation](https://docs.velociraptor.app/)
- [Velociraptor GitHub Repository](https://github.com/Velocidex/velociraptor)

---

*End of guide.*
