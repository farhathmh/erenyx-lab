# Intel NUC8 i7 (NUC1) — Primary Docker Server

## Specifications

| Component | Detail |
|-----------|--------|
| Model | Intel NUC8i7BEH |
| CPU | Intel Core i7-8559U — 4 cores / 8 threads @ 2.7GHz |
| RAM | 24GB DDR4 |
| Storage | 500GB NVMe SSD |
| OS | Ubuntu Server (bare metal) |
| Acquired | Second-hand market |

---

## Role in the Lab

Dedicated Docker host running 20 containerised services across media,
downloads, and core infrastructure categories. Chosen for its low power
consumption, small form factor, and sufficient performance for always-on
service hosting.

---

## Running Services

### Media

| Container | Purpose |
|-----------|---------|
| Plex | Primary media server |
| Jellyfin | Open source media server — Plex alternative |
| Radarr | Automated movie management |
| Sonarr | Automated TV show management |
| Bazarr | Subtitle management |
| Kometa | Media metadata manager |
| Maintainerr | Plex library maintenance |
| Notifiarr | Notification and integration client |
| Tautulli | Plex statistics and monitoring |
| Dispatcharr | IPTV and stream companion |

### Apps and Downloads

| Container | Purpose |
|-----------|---------|
| Overseerr | Media request management for Plex |
| Jellyseerr | Media request management for Jellyfin |
| Ombi | Alternative media request manager |
| Byparr | Cloudflare proxy bypass |
| qBittorrent | Torrent download client |
| SABnzbd | Usenet NZB download client |

### Core Infrastructure

| Container | Purpose |
|-----------|---------|
| Portainer | Docker container management UI |
| Homepage | Self-hosted application dashboard |
| Dozzle | Real-time Docker log viewer |
| VSCode Server | Web-based code editor |