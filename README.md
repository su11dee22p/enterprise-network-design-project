# Enterprise Network Design & Security Project

## Overview
Designed and configured a secure multi-site enterprise network for a simulated company ("TechSolutions Ltd.") using Cisco Packet Tracer. The project includes a Head Office and a Branch Office connected via a WAN serial link.

## Network Topology
- **Head Office (HQ):** IT, Finance, HR departments + Server
- **Branch Office:** Sales, Support departments
- **WAN Link:** Serial connection between HQ and Branch routers

## Technologies Implemented

### Switching
- VLANs (10, 20, 30, 40, 50)
- 802.1Q Trunking
- Inter-VLAN Routing (Router-on-a-Stick)
- Spanning Tree Protocol (PortFast)

### Routing
- OSPFv2 (IPv4)
- OSPFv3 (IPv6)
- Static Default Route

### Network Services
- DHCP (per VLAN)
- NAT/PAT (Internet access)
- DNS

### Security
- Extended ACLs (department isolation)
- Port Security (MAC address locking)
- DHCP Snooping (rogue DHCP protection)
- Dynamic ARP Inspection (ARP spoofing protection)

### IPv6
- Dual-stack (IPv4 + IPv6)
- OSPFv3

## Network Design

### VLAN Assignments
| VLAN | Department | Subnet | Location |
|------|-----------|--------|----------|
| 10 | IT | 192.168.10.0/24 | HQ |
| 20 | Finance | 192.168.20.0/24 | HQ |
| 30 | HR | 192.168.30.0/24 | HQ |
| 40 | Sales | 192.168.40.0/24 | Branch |
| 50 | Support | 192.168.50.0/24 | Branch |

### IPv6 Addressing
| VLAN | IPv6 Network |
|------|-------------|
| 10 | 2001:db8:10::/64 |
| 20 | 2001:db8:20::/64 |
| 30 | 2001:db8:30::/64 |
| 40 | 2001:db8:40::/64 |
| 50 | 2001:db8:50::/64 |
| WAN | 2001:db8:99::/64 |

## Security Policies
| Source | Destination | Action |
|--------|-------------|--------|
| HR | Finance | Deny |
| Sales | HR | Deny |
| Support | Finance | Deny |
| Any | Any | Permit |

## Key Configuration Highlights
- **Router-on-a-Stick:** Sub-interfaces with `encapsulation dot1Q` for inter-VLAN routing.
- **OSPF:** Configured on all routers with `router-id` and `network` statements.
- **NAT/PAT:** `ip nat inside source list 1 interface g0/1 overload` for internet access.
- **Layer 2 Security:** Port Security (sticky MAC), DHCP Snooping (trusted uplink), DAI (trusted uplink).

## Files
- `enterprise-network-design.pkt` – Cisco Packet Tracer project file

## Author
Sudeep Khati B.K. – MSc Cyber Security Student | CCNA
