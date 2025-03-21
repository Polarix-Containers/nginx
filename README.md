# NGINX

![Build unprivileged mainline slim, scan & push](https://github.com/Polarix-Containers/nginx/actions/workflows/build-unprivileged-mainline-slim.yml/badge.svg)
![Build unprivileged stable slim, scan & push](https://github.com/Polarix-Containers/nginx/actions/workflows/build-unprivileged-stable-slim.yml/badge.svg)

### Features & usage
- Built on upstream [NGINX images](https://github.com/nginxinc/docker-nginx), to be used as a drop-in replacement. Comes with regular rebuilds and hardened_malloc which are standard among Polarix containers.
- Adds `ca-certificates` package for MTLS setups.

### Sample Docker Compose config

```
 nginx:
    container_name: nginx
    image: ghcr.io/polarix-containers/nginx:unprivileged-slim
    restart: unless-stopped
    ports:
      - "8080:8080/tcp"
    volumes:
      - "./nginx/default.conf:/etc/nginx/conf.d/default.conf:Z,ro"
    user: "101:101"
    read_only: true
    tmpfs:
      - /var/cache/nginx:mode=0770,uid=101,gid=101,noexec,nosuid,nodev
      - /tmp:mode=0770,uid=101,gid=101,noexec,nosuid,nodev
    security_opt:
      - "no-new-privileges=true"
    cap_drop:
      - ALL
```

### Licensing
- The code in this repository is licensed under the Apache license. 😇
- These images are built on upstream images, which are under the BSD license. Copyright to the base images belongs to F5 Inc.
- Any image built by Polarix Containers is provided under the combination of license terms resulting from the use of individual packages.
