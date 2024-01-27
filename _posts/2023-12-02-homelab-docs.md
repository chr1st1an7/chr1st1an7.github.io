---
layout: post
title: HomeLab Notes
date: 2023-12-02 20:00:00 +1000
categories: homelab
tags: docs homelab linux
---
## HomeLab Projects

### Server
- Ubuntu Server as the main OS on the server
- Portainer or Dockage for managing containers
- Frigate as CCTV
- Pihole
- NGINX Proxy Manager
- Sonarr, Radarr, Bazarr, Overseer
- Home Assistant
- VPN
- FreshRSS
- Grafana
- Uptime Kuma
- Vaultwarden
- Guacamole
- Nextcloud
- Homarr
- Linkwarden


### Media Server
- TrueNAS Scale as the main OS on the Media Server
    - Use it as a NAS
    - NFS Share for Docker Volumes and storage for PCs
    - Syncthing or something similar for backups
    - Jellyfin, Photoprism
   


### Nextcloud

#### Exec into nextcloud
```bash
sudo docker exec -u 33 -it nextcloud /bin/bash
```

#### Set chunk size to 0
```bash
php occ config:app:set files max_chunk_size --value 0
```