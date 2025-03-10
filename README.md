# monitoring
# Cockpit: Installation and Plugin Activation Guide
Cockpit is a powerful web-based server management tool that simplifies the administration of Linux servers. This guide will walk you through installing Cockpit, enabling essential plugins, and optimizing it for better management.

 Install Cockpit on Ubuntu/Debian
```bash

sudo apt update
sudo apt install cockpit -y
sudo systemctl enable --now cockpit.socket

```
 Now, access Cockpit in your browser:
 ```bash
https://<server-ip>:9090
```
# 2. Installing and Enabling Cockpit Plugins
Cockpit supports multiple plugins (modules) to enhance its functionality. You can list available plugins using:

```bash
sudo apt search cockpit
```

# Install these plugins on Ubuntu/Debian

```bash
sudo apt install cockpit-machines cockpit-podman cockpit-networkmanager cockpit-storaged -y
```

```bash
sudo systemctl restart cockpit.service
```


3. Enabling Docker Management in Cockpit
Cockpit can be used to manage Docker containers if you install and configure it properly.

# Install Docker
```bash
sudo apt install docker.io -y  # Ubuntu/Debian
```
# Grant Cockpit Access to Docker
```bash
sudo usermod -aG docker $(whoami)
```
# Restart Services
```bash
sudo systemctl restart docker
sudo systemctl restart cockpit.service
```
 Now, you can manage Docker containers from Cockpit's web interface.

 # 4. Enable System Monitoring for CPU, RAM, and Disk Usage
```bash
sudo apt install cockpit-system -y  # Ubuntu/Debian
```

# 5. Setting Up Automatic Backups
If you want Cockpit to handle system backups, install rsync:

```bash
sudo apt install rsync -y  # Ubuntu/Debian
```

 # 6. Managing Users and Permissions in Cockpit
To add users to Cockpit:

```bash
sudo usermod -aG cockpit your_username

```
# 7. Changing Cockpit’s Default Port
By default, Cockpit runs on port 9090. To change it:

 Edit Cockpit’s systemd Socket Configuration
```bash

sudo nano /lib/systemd/system/cockpit.socket
```
```bash
ListenStream=9090
```
Change it to your desired port (e.g., 9091):

```bash
ListenStream=9091
```
 Apply Changes
```bash

sudo systemctl daemon-reload
sudo systemctl restart cockpit.socket
sudo systemctl restart cockpit.service
```






