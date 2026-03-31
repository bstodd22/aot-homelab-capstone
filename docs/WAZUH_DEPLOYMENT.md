# Wazuh Deployment + Inter-VLAN Routing + RDP Access

## Overview
This phase of the homelab focused on validating network segmentation, enabling controlled access between VLANs, and deploying centralized monitoring using Wazuh.

---

## Lab Architecture

- **Hypervisor:** Proxmox
- **Firewall:** pfSense (VM)
- **VLAN 10 (LAN):** 10.10.10.0/24
- **VLAN 30 (Server Network):** 10.30.30.0/24
- **Ubuntu Server:** Hosts Docker workloads and Wazuh
- **Windows Server:** Monitored endpoint (Wazuh agent installed)

---

## Objectives

- Validate inter-VLAN communication
- Configure controlled RDP access from VLAN 10 → VLAN 30
- Deploy Wazuh SIEM
- Onboard Windows Server as an agent
- Generate and observe security events

---

## Implementation

### Inter-VLAN Routing
- Configured VLAN interfaces in pfSense:
  - `vtnet1.10 → 10.10.10.1/24`
  - `vtnet1.30 → 10.30.30.1/24`
- Verified routing between networks

---

### Firewall Rules

#### LAN (VLAN 10)
Allowed traffic:
- Source: `10.10.10.0/24`
- Destination: `10.30.30.100`
- Protocol: TCP (RDP)

#### OPT1 (VLAN 30)
Allowed traffic:
- Source: `10.10.10.0/24`
- Destination: `10.30.30.100`

Key realization:
> pfSense rules apply on the interface where traffic enters

---

### RDP Access

- Enabled Remote Desktop on Windows Server
- Allowed ICMP (ping) and RDP in Windows Firewall
- Successfully established RDP session from VLAN 10 → VLAN 30

---

### Wazuh Deployment

- Installed Wazuh on Ubuntu server
- Accessed dashboard via HTTPS (port 443)
- Verified services:
  - Indexer
  - Manager
  - Dashboard

---

### Windows Agent Onboarding

- Installed Wazuh agent on Windows Server
- Configured:
  - Manager IP: `10.10.10.104`
  - Authentication key

- Started agent service
- Verified connection in Wazuh dashboard

---

## Results

- Inter-VLAN communication successfully established
- RDP access working across segmented networks
- Windows Server successfully onboarded into Wazuh
- Security events generated and visible:
  - Logon success
  - Logoff events
  - MITRE ATT&CK mapping (T1078 – Valid Accounts)

---

## Key Takeaways

- Network connectivity ≠ allowed traffic (firewall matters)
- Host-based firewalls can block valid network paths
- Understanding traffic flow is critical for troubleshooting
- Visibility (SIEM) is just as important as access

---

## Next Steps

- Add additional monitored endpoints
- Simulate attacker behavior across VLANs
- Expand detection and alerting in Wazuh
- Integrate logging into a full investigation workflow
