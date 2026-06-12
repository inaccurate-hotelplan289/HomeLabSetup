# HomeLabSetup

My personal home server setup running on a Raspberry Pi 5. All services are containerized with Docker Compose.

## Stack

| Category | Services |
|----------|----------|
| **Media** | Jellyfin, Sonarr, Radarr, Prowlarr, qBittorrent (via Gluetun VPN), Jellyseerr, FlareSolverr |
| **Cloud & Files** | Nextcloud AIO |
| **Photos** | Immich |
| **Smart Home** | Home Assistant |
| **Automation** | n8n |
| **Auth** | Authentik (SSO / 2FA) |
| **Networking** | Nginx Proxy Manager, Pi-hole, Cloudflared |
| **Monitoring** | Prometheus, Grafana, Alertmanager, Node Exporter, cAdvisor |
| **Management** | Portainer, Watchtower, Dashy |

## Structure

```
HomeLabSetup/
├── authentik/          # SSO / Identity Provider
├── cloudflared/        # Cloudflare Tunnel
├── dashy/              # Dashboard
├── homeassistant/      # Smart Home
├── immich/             # Photo Backup
├── media/              # Media Stack (Jellyfin, *arr, qBittorrent via VPN)
├── monitoring/         # Prometheus, Grafana, Alertmanager
├── n8n/                # Workflow Automation
├── npm/                # Nginx Proxy Manager
├── pihole/             # DNS / Ad Blocker
└── portainer/          # Docker Management UI
```

## Getting Started

1. Clone the repo
2. Copy `.env.example` to `.env` in each service directory and fill in your values
3. Start services with `docker compose up -d`

Each service directory contains its own `docker-compose.yml` and a `.env.example` documenting required variables.

## Prerequisites

- Docker & Docker Compose
- ProtonVPN account (for the media stack VPN)
- Cloudflare account + domain (for Cloudflared tunnel)
- Telegram bot (for Alertmanager notifications)

## Storage Layout

```
/mnt/ssd/    # Fast storage (configs, databases)
/mnt/hdd/    # Bulk storage (media files, Nextcloud data)
```
