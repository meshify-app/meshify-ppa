## Welcome to the Meshify PPA

You can use this repo to install the meshify-client for debian linux distros.

```shell
curl -s --compressed https://meshify-app.github.io/meshify-ppa/KEY.gpg | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/meshify.list https://meshify-app.github.io/meshify-ppa/meshify.list
sudo apt update

# Install meshify-client
sudo apt install meshify-client


# Update the config
sudo mkdir -p /etc/meshify
sudo nano /etc/meshify/meshify-client.config.json

{
    "MeshifyHost": "https://my.meshify.app",
    "HostID": "",
    "ApiKey": "",
    "CheckInterval" : 10,
    "SourceAddress" : "0.0.0.0",
    "quiet" : true,
    "debug" : false
}
Update the HostID and ApiKey from your meshify control panel for the host.


# Enable and start the service
sudo systemctl enable meshify
sudo systemctl start meshify

```

