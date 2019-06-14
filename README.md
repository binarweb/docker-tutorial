# Docker tutorial

Installation will take place on a Digital Ocean droplet with Ubuntu 18.04  

## Installing some tools (optional)

```bash
apt update
apt install git mc htop screen -y
```

## Install docker

```bash
apt update
apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
apt update
apt-cache policy docker-ce
apt install docker-ce -y
```

To test the status of docker service:  
`systemctl status docker`

