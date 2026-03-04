# Network Architecture

## Infrastructure

Hypervisor:
- Proxmox

Firewall:
- pfSense (VM)

Switch:
- Managed switch with 802.1Q VLAN trunking

Server:
- Ubuntu Server running Docker

Application:
- Internal helpdesk portal (Node.js container)

---

## VLAN Design

### VLAN 10 – Internal LAN
Subnet: 10.10.10.0/24

Devices:
- Admin workstation
- Testing workstation

---

### VLAN 30 – Server Network
Subnet: 10.30.30.0/24

Devices:
- Ubuntu server
- Docker containers
- Internal web application

---

## Routing

pfSense performs inter-VLAN routing.

Firewall rules explicitly control which VLANs can communicate.

---

## Security Model

Segmentation ensures:

- Servers are isolated from user devices
- Cross-network access requires firewall rules
- Potential compromises are contained within their VLAN
