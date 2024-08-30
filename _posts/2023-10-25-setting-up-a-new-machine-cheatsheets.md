---
layout: post
title: Setting up a new machine - Cheatsheets
date: 2023-10-25 13:00:00 +2000
categories: homelab
tags: docs homelab linux
---
## Updating and upgrading Ubuntu
```shell
sudo apt update -y && sudo apt upgrade -y
```

## Install a clean installation of Docker

Remove previous/old Docker packages:
```shell
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

Run the official Docker Install Script
```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

### Install Portainer (optional)

Create a docker volume for Portainer:
```shell
docker volume create portainer_data
```
Install Portainer:

```shell
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```


### Install Watchtower (optional)

Install Watchtower to auto-update containers
```shell
docker run -d \
  --name watchtower \
  -v /var/run/docker.sock:/var/run/docker.sock \
  containrrr/watchtower --interval 30
```
