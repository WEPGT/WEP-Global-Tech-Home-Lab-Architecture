# WEP Global Tech Home Lab

This project documents my enterprise-style home lab designed to simulate real-world infrastructure environments. The lab focuses on networking, virtualization, identity management, and application hosting using technologies commonly found in production environments.

The environment is built around a layered architecture consisting of **network**, **infrastructure**, and **application tiers**. Secure remote access is provided through a **WireGuard VPN connected to a MikroTik firewall**, allowing centralized management through a custom-built command portal.

Core infrastructure services include **Proxmox virtualization**, **Active Directory domain services**, and **TrueNAS storage**. Application services run on dedicated virtual machines and include custom Node.js tools designed to support infrastructure management and automation.

---

# Table of Contents

- Architecture
- Architecture Layers
- Technology Stack
- Infrastructure Servers
- HomeExp Application
- Remote Access Workflow
- Project Goals
- Roadmap

---

# Architecture

Below is the high-level architecture of the WEP Global Tech Home Lab environment.

```mermaid
flowchart TD

Internet[Internet]

Router[MikroTik Router<br>192.168.88.1<br>WireGuard VPN]

LAN[LAN Network<br>192.168.88.0/24]

Portal[Portal Server<br>192.168.88.231<br>WEP Command Portal]

Proxmox[Proxmox Hypervisor<br>192.168.88.200]

DC[Domain Controller<br>192.168.88.230]

ServiceCore[service-core-01<br>192.168.88.155]

HomeExp[HomeExp Application<br>Node.js<br>Port 4000]

Internet --> Router
Router --> LAN

LAN --> Portal
LAN --> Proxmox
LAN --> DC

Proxmox --> ServiceCore
ServiceCore --> HomeExp

Portal --> Proxmox
Portal --> DC
Portal --> HomeExp
