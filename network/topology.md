# Network Topology

## Overview

The Erenyx Lab network is built around a constraint — no owned internet
connection. The upstream internet arrives via shared WiFi, then enters an
Alpine WiFi Bridge VM with PCIe WiFi passthrough. That VM performs a NAT
bridge from WiFi to eth0 toward OPNsense WAN. OPNsense is the WAN edge
firewall for the full lab, and LAN services are distributed through Proxmox
virtual networking to the physical access layer.

---

## Hardware

| Device                | Role                                                                  |
| --------------------- | --------------------------------------------------------------------- |
| Alpine WiFi Bridge VM | WiFi uplink VM with PCIe WiFi passthrough and WiFi-to-eth0 NAT bridge |
| OPNsense Firewall VM  | WAN edge firewall and LAN gateway for the entire lab                  |
| TP-Link Archer AX23   | Access point and LAN switch for wired and wireless clients            |

---

## Traffic Flow

1. Shared WiFi -> Alpine VM WiFi interface
2. Alpine VM -> NAT bridge to eth0
3. eth0 -> OPNsense WAN
4. OPNsense LAN -> Proxmox management virtual bridge
5. Proxmox bridge uplink -> TP-Link Archer AX23 AP/switch
6. Endpoints -> NAS, NUC1, NUC2, RPi4B, and laptop clients on Erenyx WiFi

---

## Network Segments

| Segment      | Interface                      | Details                                                        |
| ------------ | ------------------------------ | -------------------------------------------------------------- |
| WAN Source   | Alpine VM WiFi interface       | Connects to shared upstream WiFi                               |
| NAT Bridge   | Alpine VM eth0                 | Forwards uplink traffic to OPNsense WAN                        |
| WAN Edge     | OPNsense WAN                   | Firewall boundary for the full lab                             |
| LAN Gateway  | OPNsense LAN on Proxmox bridge | Routes traffic to internal services and client network         |
| Access Layer | TP-Link AX23 AP/switch uplink  | Physical access for NAS, NUC1, NUC2, RPi4B, and laptop clients |

---

## Architecture Notes

A legacy wireless uplink implementation is still documented as a project
reference, but it is not the current live routing path. The active runtime
path is Alpine bridge plus OPNsense WAN edge.

> Legacy implementation repository -> [wireless-uplink-bridge-docs](https://github.com/farhathmh/openwrt-wifi-as-wan)

---

## The Problem and Solution

> Full documented solution history -> [wireless-uplink-bridge-docs](https://github.com/farhathmh/openwrt-wifi-as-wan)

Standard home routers expect a wired WAN connection from an ISP modem.
The building internet is only available via WiFi with no physical access
to an upstream router. The current solution uses a dedicated Alpine VM to
ingest WiFi and pass WAN connectivity to OPNsense, which then secures and
routes the entire lab network.

---

## Planned

- VLAN segmentation by device role
- Dedicated IoT VLAN isolation
- Firewall rules between VLANs
- Network monitoring and traffic visibility
- Wireless uplink bridge series documentation for additional architecture variants
