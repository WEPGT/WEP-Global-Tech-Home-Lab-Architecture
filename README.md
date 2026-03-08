# WEP Global Tech Home Lab

This repository documents my enterprise-style home lab used to simulate real-world IT infrastructure environments.

The lab is designed to practice systems administration, networking, virtualization, and automation using technologies commonly found in production environments.

---

# Infrastructure Overview

The environment is built using a layered architecture consisting of networking, virtualization infrastructure, and application services.

Secure remote access is provided through a WireGuard VPN connected to a MikroTik firewall.

Core infrastructure services include Proxmox virtualization, Active Directory domain services, and TrueNAS storage.

---
# Infrastructure Screenshots

## Proxmox Virtualization Host

![Proxmox Dashboard](images/proxmox-dashboard.png)

---

## Virtual Machine Inventory

![VM Inventory](images/vm-inventory.png)

---

## Active Directory Domain

![Active Directory](images/active-directory-domain.png)

---

## Network Infrastructure

![MikroTik Router](images/mikrotik-wireguard.png)

---

## Linux Server Monitoring / Glances

![Glances Monitoring](images/linux-server-monitoring.png)
# Architecture

```mermaid
flowchart TD

Internet --> MikroTikRouter

MikroTikRouter --> LAN

LAN --> ProxmoxHost
LAN --> StorageServer

ProxmoxHost --> DomainController
ProxmoxHost --> InfrastructureVMs
ProxmoxHost --> ApplicationVMs

StorageServer --> TrueNAS
```

---

# Infrastructure Inventory

| System | Role | Operating System | IP Address |
|------|------|------|------|
| Proxmox Host | Virtualization Hypervisor | Debian / Proxmox VE | 192.168.88.200 |
| DC1 | Active Directory Domain Controller | Ubuntu Server + Samba AD | 192.168.88.230 |
| service-core | Application / Services Server | Ubuntu Server | 192.168.88.xxx |
| Portal | Infrastructure Management Portal | Node.js / Linux | 192.168.88.xxx |
| Home Server | Storage / File Server | Windows 11 | 192.168.88.50 |
| MikroTik Router | Firewall / Routing / VPN | RouterOS | 192.168.88.1 |
# Technology Stack
## Networking

- MikroTik RouterOS

- WireGuard VPN

- VLAN segmentation

## Virtualization

- Proxmox VE

- Linux Virtual Machines

## Identity

- Active Directory Domain Services

- Internal DNS

## Storage

- TrueNAS

- Network File Shares

## Applications

- Node.js infrastructure tools

- Internal management portal

- Monitoring utilities

## Project Goals

-  Build hands-on enterprise infrastructure experience
-  Practice network design and segmentation
-  Develop infrastructure automation tools
-  Document real-world troubleshooting scenarios

## Future Roadmap

- Centralized monitoring

- Infrastructure automation

- Containerized services

- Internal helpdesk system

- Advanced network segmentation
