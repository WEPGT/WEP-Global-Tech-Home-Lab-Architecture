# WEP Global Tech Home Lab

This project documents my enterprise-style home lab designed to simulate real-world infrastructure environments. The lab focuses on networking, virtualization, identity management, and application hosting using technologies commonly found in production environments.

The environment is built around a layered architecture consisting of **network**, **infrastructure**, and **application tiers**. Secure remote access is provided through a **WireGuard VPN connected to a MikroTik firewall**, allowing centralized management through a custom-built command portal.

Core infrastructure services include **Proxmox virtualization**, **Active Directory domain services**, and **TrueNAS storage**. Application services run on dedicated virtual machines and include custom Node.js tools designed to support infrastructure management and automation.

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
Architecture Layers

Network Layer

MikroTik RouterOS

WireGuard VPN

Firewall / NAT

Infrastructure Layer

Proxmox Virtualization

Active Directory

TrueNAS Storage

Application Layer

WEP Command Portal

HomeExp Application

nginx Web Services

Technology Stack

Technologies used in this environment include:

MikroTik RouterOS

WireGuard VPN

Proxmox VE

Linux Servers

Active Directory

TrueNAS Storage

nginx

Node.js

Infrastructure Servers
MikroTik Router
IP: 192.168.88.1
Role:
• Firewall
• VPN Server
• Internet Gateway
Portal Server
IP: 192.168.88.231
Role:
• WEP Global Tech Command Portal
• Infrastructure dashboard
• Entry point for internal services
Proxmox Hypervisor
IP: 192.168.88.200
Role:
• Virtual machine host
• Infrastructure virtualization
Domain Controller
IP: 192.168.88.230
Role:
• Active Directory
• Internal DNS
• Authentication services
service-core-01
IP: 192.168.88.155
Role:
• Application server
• nginx reverse proxy
• HomeExp custom application
HomeExp Application

HomeExp is a custom Node.js application designed to support internal infrastructure management.

Location: /srv/HomeExp
Port: 4000
Runtime: Node.js

Purpose:

Internal application hosting

Portal page generation

Infrastructure management tools

Remote Access Workflow
Remote Laptop
      │
WireGuard VPN
      │
MikroTik Router
      │
LAN Network
      │
WEP Command Portal
      │
Infrastructure & Applications

The command portal acts as a single pane of glass for managing the environment.

Project Goals

The goal of this lab is to build hands-on experience designing and operating enterprise-style infrastructure.

Current objectives:

Build layered infrastructure architecture

Implement secure VPN remote access

Manage virtualized services

Develop internal applications

Document system architecture

Roadmap

Future improvements planned for this environment.

Networking

VLAN segmentation

Advanced firewall policies

Network monitoring

Infrastructure

VM replication

Automated backups

Infrastructure monitoring

Applications

Expand HomeExp application

Add health dashboards

Centralized logging
