# Network Diagram

Logical layout of the homelab environment.

```
                Internet
                    │
                    │
              ┌──────────┐
              │  pfSense │
              │ Firewall │
              └─────┬────┘
                    │
            802.1Q VLAN Trunk
                    │
             ┌────────────┐
             │ Managed    │
             │ Switch     │
             └─────┬──────┘
                   │
        ┌──────────┴───────────┐
        │                      │

   VLAN 10                VLAN 30
 Internal LAN           Server Network
 10.10.10.0/24          10.30.30.0/24

   Workstations          Ubuntu Server
                         Docker
                         Node.js IT Portal
```

## Security Controls

Segmentation is enforced using:

- VLAN isolation
- pfSense firewall rules
- Inter-VLAN routing restrictions
- Outbound NAT

## Purpose

The lab simulates an enterprise-style segmented network where:

- user devices are separated from servers
- lateral movement can be tested
- firewall segmentation can be validated
