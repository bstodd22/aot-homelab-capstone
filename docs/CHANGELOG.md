# Homelab Changelog

## 2026-03-03

Initial homelab architecture completed.

Infrastructure deployed:

- Proxmox hypervisor
- pfSense firewall VM
- Managed switch with VLAN trunking
- Ubuntu server running Docker
- Node.js helpdesk portal container

Networking configured:

- VLAN 10 – Internal LAN (10.10.10.0/24)
- VLAN 30 – Server network (10.30.30.0/24)
- Inter-VLAN routing via pfSense
- Outbound NAT verified

Troubleshooting included:

- APIPA addresses caused by incorrect VLAN tagging
- Trunk port configuration issues
- PVID alignment errors
- Missing pfSense firewall rules
