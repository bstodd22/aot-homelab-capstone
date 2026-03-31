# AOT Homelab Capstone

This repository documents an ongoing cybersecurity homelab designed to simulate a segmented enterprise environment similar to operational technology (AOT) infrastructure.

The lab focuses on network segmentation, internal service deployment, security monitoring, and controlled vulnerability testing.

---

## Infrastructure

### Hypervisor
- Proxmox

### Firewall
- pfSense (virtual machine)

### Networking
- Managed switch with 802.1Q VLAN trunking

### Servers
- Ubuntu Server (Docker host)
- Windows Server (monitored endpoint)

### Application
- Node.js internal helpdesk portal (lab-only)

---

## Network Architecture

VLAN segmentation is enforced using pfSense.

| VLAN | Purpose | Subnet |
|------|--------|--------|
| VLAN 10 | Internal LAN | 10.10.10.0/24 |
| VLAN 30 | Server Network | 10.30.30.0/24 |

Traffic between VLANs requires explicit firewall rules and is intentionally restricted.

---

## Services Deployed

### Ubuntu Server (Docker host)
- Internal helpdesk portal (Node.js)
- Wazuh SIEM (manager + dashboard)
- Future logging / monitoring stack

### Windows Server
- RDP-enabled system in isolated VLAN
- Wazuh agent installed for endpoint monitoring

---

## Security Monitoring

Wazuh is deployed for centralized logging and detection.

Current capabilities:
- Windows authentication monitoring (logon/logoff events)
- MITRE ATT&CK mapping (e.g., T1078 – Valid Accounts)
- Event correlation across systems
- Dashboard visualization of activity

---

## Current Work Completed

- pfSense deployed on Proxmox
- Managed switch configured with VLAN trunking
- VLAN 10 and VLAN 30 networks operational
- Inter-VLAN routing configured and validated
- Firewall rules implemented for controlled access
- RDP access established from VLAN 10 → VLAN 30
- Internal web application deployed in Docker
- Wazuh SIEM deployed on Ubuntu server
- Windows Server onboarded as a monitored agent
- Security events successfully generated and analyzed

---

## Troubleshooting Highlights

- APIPA (169.x.x.x) addresses caused by incorrect VLAN tagging
- PVID misconfiguration on switch ports
- Trunk vs access port confusion
- Firewall rules applied on incorrect interfaces
- ICMP and RDP blocked by host-based firewall
- Wazuh agent registration and authentication issues

---

## Planned Work

Next phases of the project include:

- Additional endpoint onboarding (multi-agent visibility)
- Simulated attacker → victim traffic across VLANs
- Detection engineering and alert tuning in Wazuh
- IDS/IPS integration
- Web application vulnerability testing (auth, IDOR, uploads)
- Segmentation validation under attack scenarios
- Cloud integration for hybrid environment testing

---

## Purpose

This lab is designed to develop practical experience in:

- Network segmentation and VLAN design
- Firewall rule implementation and traffic control
- Infrastructure troubleshooting and debugging
- Security monitoring and SIEM workflows
- Web application security testing
- Detection and investigation processes

The goal is to understand how security controls interact in a realistic, segmented environment—not just how to deploy them.
