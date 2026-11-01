# IRC Monitor

A lightweight IRC monitoring application for IEGMC.org.

## Prerequisites: Installing Docker on Debian 13

Run the following commands as `root` (or with `sudo`) to install the official Docker repository and packages on Debian 13:

```bash
apt update
apt install ca-certificates curl
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
chmod a+r /etc/apt/keyrings/docker.asc
tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/debian
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
apt update
apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Quick Start (Docker Compose)

Create a `docker-compose.yml` file on your host machine:

```yaml
version: '3.8'
services:
  irc-monitor:
    image: ghcr.io/YOUR_GITHUB_USERNAME/irc-monitor:20261031
    container_name: irc-monitor
    ports:
      - "38080:8080"
    restart: unless-stopped
```

Run the container:

```bash
docker compose up -d
```
