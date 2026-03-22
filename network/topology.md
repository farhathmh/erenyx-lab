# Network Topology

## Overview

The Erenyx Lab network is built around a constraint — no owned internet
connection. The upstream internet arrives via WiFi. The solution was to
flash OpenWrt on a TP-Link AX23 and configure WiFi as WAN, feeding all
homelab devices through wired LAN ports.

---

## Hardware

| Device | Role |
|--------|------|
| TP-Link AX23 | Core router running OpenWrt CE |

---

## Network Segments

| Segment | Interface | Details |
|---------|-----------|---------|
| WAN | wlan0 | Upstream WiFi — connects to building WiFi as internet source |
| LAN | eth0-3 | All homelab devices — HP Z440, NUC1, NUC2, RPi4B |

---

## The Problem and Solution

> Full documented solution → [homelab-network-setup](https://github.com/farhathmh/homelab-network-setup)

Standard home routers expect a wired WAN connection from an ISP modem.
The building internet was only available via WiFi with no physical access
to the upstream router. The solution was OpenWrt which supports WiFi as
WAN — the router associates with the upstream WiFi as a client and routes
that connection to all wired LAN devices.

---

## Planned

- VLAN segmentation by device role
- Dedicated IoT VLAN isolation
- Firewall rules between VLANs
- Network monitoring and traffic visibility