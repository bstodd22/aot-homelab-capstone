# aot-homelab-capstone
Cybersecurity homelab simulating a segmented enterprise environment with VLANs, pfSense firewalling, internal services, and security testing of an intentionally vulnerable application.

# AOT Homelab Capstone

This repository documents an ongoing cybersecurity homelab designed to simulate a segmented enterprise environment similar to operational technology (AOT) infrastructure.

The lab focuses on network segmentation, internal service deployment, security monitoring, and controlled vulnerability testing.

---

## Infrastructure

**Hypervisor**
- Proxmox

**Firewall**
- pfSense (virtual machine)

**Networking**
- Managed switch with 802.1Q VLAN trunking

**Server**
- Ubuntu Server running Docker

**Application**
- Node.js internal helpdesk portal (lab-only)

---

## Network Architecture

VLAN segmentation is enforced using pfSense.

| VLAN | Purpose | Subnet |
|-----|------|------|
| VLAN 10 | Internal LAN | 10.10.10.0/24 |
| VLAN 30 | Server Network | 10.30.30.0/24 |

Traffic between VLANs requires explicit firewall rules.

---

## Services Deployed

**Ubuntu Server (Docker host)**

Running containers including:

- Internal helpdesk portal (Node.js)
- Future logging / monitoring stack

---

## Current Work Completed

- pfSense deployed on Proxmox
- Managed switch configured with VLAN trunking
- VLAN 10 and VLAN 30 networks operational
- Inter-VLAN routing configured
- NAT verified
- Internal web application deployed in Docker

Troubleshooting included:

- APIPA (169.x.x.x) addresses caused by incorrect VLAN tagging
- PVID configuration errors
- Trunk vs access port confusion
- Missing interface firewall rules

---

## Planned Work

Next phases of the project include:

- Centralized logging
- IDS/IPS monitoring
- Simulated internal attack scenarios
- Testing segmentation enforcement
- Hardening the internal application
- Extending the environment into cloud infrastructure

---

## Purpose

This lab is designed to develop practical experience in:

- Network segmentation
- Firewall rule design
- Infrastructure troubleshooting
- Web application security testing
- Detection and monitoring workflows

The goal is to understand how security controls operate together in a realistic environment.
