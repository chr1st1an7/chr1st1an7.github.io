---
layout: post
title: Traefik Deployment and Usage
date: 2024-03-22 13:00:00 +2000
categories: homelab
tags: docs homelab traefik
---

## Deploying Traefik





## Configuring an external service
If we want to add a service to Traefik that isn't on the same machine with Traefik, we need to do it in Traefik's config.yml file.

First, we add the entrypoints for the service:

> Make sure to change the service's name, domain, and URL 
{: .prompt-info }

```yaml
NAME:
    entryPoints:
    - "https"
    rule: "Host(`DOMAIN`)"
    middlewares:
    - default-headers
    - https-redirectscheme
    tls: {}
    service: NAME
```

Then we add the URL to the service:
```yaml 
NAME:
    loadBalancer:
    servers:
        - url: "https://192.168.1.3:8006"
    passHostHeader: true
```
And after we do that and save the file, our service will be exposed on our domain without restarting Traefik :)

## Configuring an internal service
If we want to add a service that is on the same machine with Traefik, we can do it in the service's docker compose file.

First, we want to add our service to our *proxy* network:
```yaml
networks:
    proxy:
```

And add the network at the end of the docker compose file:
```yaml
networks:
  proxy:
    external: true
```

And finally add the labels that Traefik recognizes:

> Make sure to change the name of your service in the code, the domain and the port the service is running on 
{: .prompt-info }

```yaml
labels:
      - "traefik.enable=true"
      - "traefik.http.routers.NAME.entrypoints=http"
      - "traefik.http.routers.NAME.rule=Host(`DOMAIN`)"
      - "traefik.http.middlewares.NAME-https-redirect.redirectscheme.scheme=https"
      - "traefik.http.routers.NAME.middlewares=NAME-https-redirect"
      - "traefik.http.routers.NAME-secure.entrypoints=https"
      - "traefik.http.routers.NAME-secure.rule=Host(`DOMAIN`)"
      - "traefik.http.routers.NAME-secure.tls=true"
      - "traefik.http.routers.NAME-secure.service=NAME"
      - "traefik.http.services.NAME.loadbalancer.server.port=PORT"
      - "traefik.docker.network=proxy"
```