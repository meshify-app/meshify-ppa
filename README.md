## Welcome to the Meshify PPA

You can use this repo to install the meshify-client for debian linux distros.

```shell
curl -s --compressed https://meshify-app.github.io/meshify-ppa/KEY.gpg | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/my_file_list.list https://meshify-app.github.io/meshify-ppa/my_file_list.list
sudo apt update

# Install meshify-client
sudo apt install meshify-client

# Update the config
sudo nano /etc/meshify/meshify-client.config.json

# Enable and start the service
sudo systemctl enable meshify
sudo systemctl start meshify

```

