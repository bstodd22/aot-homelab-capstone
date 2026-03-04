# aot-homelab-capstone
Cybersecurity homelab simulating a segmented enterprise environment with VLANs, pfSense firewalling, internal services, and security testing of an intentionally vulnerable application.

# AOT Homelab Capstone (WGU)

This repository tracks an ongoing cybersecurity homelab project designed to simulate an AOT-style enterprise environment:
segmented networks, controlled inter-VLAN access, centralized logging/detection, and a deliberate insecure “vibe-coded” internal
application used for realistic testing and remediation.

## Objectives
- Design and operate a segmented network with pfSense + VLANs
- Validate segmentation with explicit firewall rules and testing
- Deploy an intentionally insecure internal helpdesk app (Node.js) for web pentesting practice
- Add detection + logging to support investigation workflows (SIEM/EDR-style)
- Extend into cloud to simulate hybrid security controls

## Current Lab Architecture
- Hypervisor: Proxmox
- Firewall: pfSense (VM)
- Switching: Managed switch with 802.1Q trunking
- VLANs:
  - VLAN 10: Internal LAN (10.10.10.0/24)
  - VLAN 30: Server network (10.30.30.0/24)
- Routing: Inter-VLAN routing via pfSense with explicit allow/deny rules
- NAT: Outbound NAT configured and verified

## Work Completed (Highlights)
- pfSense deployed and routed VLAN 10 / VLAN 30
- 802.1Q trunk configured to managed switch
- Troubleshot:
  - APIPA/self-assigned IPs from incorrect tagging/PVID
  - trunk/access port confusion (L2 vs L3 issues)
  - missing interface-level firewall rules
- Deployed internal “Alliah IT Portal” helpdesk app (Node.js) in lab

## Testing Plan
### Web App
- Authentication + session handling review
- Authorization checks (IDOR-style access patterns)
- Input validation (XSS/SQLi patterns depending on stack)
- File upload handling and storage controls

### Network / Segmentation Validation
- Verify intended east/west traffic paths
- Attempt lateral movement simulation across VLANs
- Confirm logging visibility of scans/blocked traffic

## Detection / Logging Roadmap
- Centralize logs (pfSense + Linux + Windows)
- Add IDS/IPS visibility (Suricata/Zeek) where appropriate
- Build basic detections + investigation notes

## Repo Navigation
- `lab/` network design, configs, inventory
- `app/` application and supporting infra notes
- `pentest/` test plans, findings, remediation, evidence
- `detection/` logging + detection configs and notes
- `cloud/` hybrid extension design + IaC notes
- `docs/` scope, status, threat model, changelog

## Disclaimer
This lab is for defensive learning and authorized testing in a controlled environment only. Do not expose intentionally vulnerable services to the public internet.
