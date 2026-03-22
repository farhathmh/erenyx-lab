# Docker Stack — NUC1

## Overview

NUC1 runs Ubuntu Server bare metal with Docker managing 20 containerised
services. All services are defined using Docker Compose for reproducibility
and easy redeployment.

---

## Stack Categories

### Media (10 services)
Plex, Jellyfin, Radarr, Sonarr, Bazarr, Kometa,
Maintainerr, Notifiarr, Tautulli, Dispatcharr

### Apps and Downloads (6 services)
Overseerr, Jellyseerr, Ombi, Byparr, qBittorrent, SABnzbd

### Core Infrastructure (4 services)
Portainer, Homepage, Dozzle, VSCode Server

---

## Management

| Tool | Purpose |
|------|---------|
| Portainer | GUI management of all containers |
| Dozzle | Real-time log monitoring per container |
| Homepage | Unified dashboard showing status of all services |

---

## Planned

- Centralised monitoring with Prometheus and Grafana
- Automated container update notifications
- Offsite backup of persistent container volumes to TrueNAS