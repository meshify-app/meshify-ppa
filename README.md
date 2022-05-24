## Welcome to the Meshify PPA

You can use this repo to install the meshify-client and meshifyapp for debian linux distros.  This repo will install meshify for amd64, arm64, and armv7l (raspberry pi) architectures.

If you are running a linux server and no desktop, you only need to install the meshify-client and follow the instructions below. Resolvconf is needed for WireGuard DNS functionality. Rdesktop enables RDP functionality in the meshify agent.

```
curl -s --compressed https://ppa.meshify.app/KEY.gpg | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/meshify.list https://ppa.meshify.app/meshify.list
sudo apt update

# Install wireguard if not already installed
sudo apt install wireguard resolvconf rdesktop

# Install meshify-client
sudo apt install meshify-client

# Update the config
# Create a host (manually) on https://my.meshify.app and grab the config settings from it
sudo nano /etc/meshify/meshify-client.config.json

{
    "MeshifyHost": "https://my.meshify.app",
    "HostID": "",
    "ApiKey": ""
}
# Update the HostID and ApiKey from your meshify control panel for the host.
# Enable and start the service
sudo systemctl enable meshify
sudo systemctl start meshify

# Install meshify agent
sudo apt install meshifyagent
meshifyagent &

# Enable IP forwarding for subnet routing or VPN tunneling
sudo nano /etc/sysctl.conf

In the file, uncomment the line below to enable IP forwarding

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Ctrl-X to save the file, then reboot the system.

sudo reboot now
```
