## Welcome to the Meshify PPA

You can use this repo to install the meshify-client and meshifyapp for debian linux distros.  This repo will install meshify for amd64, arm64, and armv7l (raspberry pi) architectures.

```shell
curl -s --compressed https://ppa.meshify.app/KEY.gpg | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/meshify.list https://ppa.meshify.app/meshify.list
sudo apt update

# Install wireguard if not already installed
sudo apt install wireguard resolvconf

# Install meshify-client
sudo apt install meshify-client

# Install meshify agent.  It installs to the Network ("Internet") group, next to the browser.
sudo apt install meshifyapp

# Update the config
sudo mkdir -p /etc/meshify
sudo nano /etc/meshify/meshify-client.config.json

{
    "MeshifyHost": "https://my.meshify.app",
    "HostID": "",
    "ApiKey": ""
}
Update the HostID and ApiKey from your meshify control panel for the host.

# Enable and start the service
sudo systemctl enable meshify
sudo systemctl start meshify

# Enable IP forwarding for subnet routing or VPN tunneling
sudo nano /etc/sysctl.conf

In the file, uncomment the line below to enable IP forwarding

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

Ctrl-X to save the file, then reboot the system.

sudo reboot now

```

