<div align="center">

# Erenyx Lab

**A personal infrastructure environment built for learning, breaking, and solving real problems.**
**Every problem documented. Every solution linked.**

![Status](https://img.shields.io/badge/Status-Active-00B4D8?style=for-the-badge)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![OpenWrt](https://img.shields.io/badge/OpenWrt-00B5E2?style=for-the-badge&logo=openwrt&logoColor=white)
![TrueNAS](https://img.shields.io/badge/TrueNAS-0095D5?style=for-the-badge&logo=truenas&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

---

## What is Erenyx Lab

Erenyx Lab is my personal homelab — a physical infrastructure environment
built entirely from second-hand hardware, designed for hands-on learning,
real-world problem solving, and running self-hosted services.

Every device has a purpose. Every problem encountered is documented with its
full context, research process, and solution. This is not a simulated
environment. This is real hardware solving real problems.

---

## Hardware Inventory

| Device | Role | CPU | RAM | Storage |
|--------|------|-----|-----|---------|
| HP Z440 Workstation | Proxmox hypervisor | Xeon E5-2698 v4 (20c/40t) | 64GB DDR4 ECC | 960GB SSD (VMs) + 1.5TB HDD (ISO/backups) + 1TB HDD (TrueNAS passthrough) |
| Intel NUC8 i7 (NUC1) | Primary Docker server | Core i7-8559U | 24GB | 500GB NVMe |
| Intel NUC8 i3 (NUC2) | Testing and experiments | Core i3-8109U | 16GB | 500GB NVMe + 500GB SSD |
| Raspberry Pi 4B | Edge testing / lightweight services | Cortex-A72 (4c) | 8GB | 64GB MicroSD |
| TP-Link AX23 (OpenWrt) | Core router / network controller | — | — | Custom OpenWrt firmware |

> All hardware acquired from the second-hand market — proof that a serious
> lab does not require a serious budget.

---

## What is Running

### HP Z440 — Proxmox Host

| VM | Purpose | Status |
|----|---------|--------|
| EVE-NG CE | Network simulation and CCNA/CCNP lab environment | Active |
| TrueNAS CE | Network attached storage with PCIe passthrough HDD | Active |

> Planning: Additional 1TB HDD for TrueNAS RAID testing and redundancy experiments.

### NUC1 — Docker Server

Running 20 containerised services across three categories:

**Media stack:** Plex, Jellyfin, Radarr, Sonarr, Bazarr, Kometa,
Maintainerr, Notifiarr, Tautulli, Dispatcharr

**Apps and downloads:** Overseerr, Jellyseerr, Ombi, Byparr,
qBittorrent, SABnzbd

**Core infrastructure:** Portainer, Homepage, Dozzle, VSCode Server

> Full Docker stack documentation → [services/docker-stack.md](services/docker-stack.md)

### NUC2 and Raspberry Pi 4B

Currently used for testing and disposable experiments.
Future role being planned as the lab evolves.

---

## Network

| Segment | Details |
|---------|---------|
| Router | TP-Link AX23 running OpenWrt custom firmware |
| WAN | Upstream WiFi connection — no owned ISP line |
| LAN | All homelab devices on wired LAN |
| VLANs | Planned — segmentation by device role |

> Full network topology and OpenWrt configuration → [network/topology.md](network/topology.md)

---

## Documented Problems and Solutions

The core of this repository. Every real problem encountered in this lab
has a dedicated repository with full documentation.

| Problem | Solution Repo | Status |
|---------|--------------|--------|
| No owned internet — needed WiFi as WAN to feed wired homelab LAN | [homelab-network-setup](https://github.com/farhathmh/homelab-network-setup) | In Progress |

> More solutions added as the lab grows.

---

## Goals

- [ ] Full VLAN segmentation across all devices
- [ ] Centralised monitoring — Grafana and Prometheus across all nodes
- [ ] TrueNAS RAID setup and redundancy testing
- [ ] Automated backup solution across all nodes
- [ ] CI/CD pipeline for homelab configuration management
- [ ] Document every problem and solution as it happens

---

## Hardware Details

- [HP Z440 — Proxmox Host](hardware/hp-z440.md)
- [NUC1 — Docker Server](hardware/nuc1-docker-server.md)
- [NUC2 — Testing Node](hardware/nuc2-testing.md)
- [Raspberry Pi 4B](hardware/rpi4b.md)

---

<div align="center">
<sub>Built and maintained by <a href="https://github.com/farhathmh">Farhath Manas</a>
 — because the best way to learn is to build it yourself.</sub>
</div>