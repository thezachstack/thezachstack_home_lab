# LAB - AS-BUILT (Verified Snapshot)
Status: CURRENT STATUS (AS-BUILT, VERIFIED)
Date: 2026-02-04
Author: thezachstack

## Physical / Hardware
- HP ProLiant DL360 Gen9
  - Racked, powered, reachable
  - No hypervisor installed yet
- Cisco ISR 2811 router
  - Powered, basic config, reachable
- Cisco Catalyst 3550 switch
  - Powered, basic config, reachable
- Cisco Aironet 2802i AP
  - Powered via AIR-PWRINJ6
- Dell OptiPlex workstation
  - Ubuntu 24.04 — used as management/admin host
- 12U rack with PDU
  - Power cabling complete
- Flat L2 network
  - 192.168.100.0/24

## Virtualization / Cloud
- Apache CloudStack Management Server
  - Running on Debian
  - Service starts cleanly
  - GUI reachable at: http://192.168.100.51:8080/client
  - MariaDB running locally, CloudStack DB user functional
  - Problem: CloudStack admin credentials unknown / inaccessible
  - GUI reachable but login blocked
  - No hypervisors registered
  - No compute, storage, or network zones configured

## Networking
- Basic IP connectivity confirmed between router, switch, CloudStack host, and workstation
- No VLANs, no dynamic routing, no WAN simulation yet

## Pending Tasking (Order Matters)
### Immediate (Blocking)
1. Recover or reset CloudStack admin login
2. Verify CloudStack persistence across reboot
3. Confirm CloudStack DB and config alignment post-recovery

### Short-term (Foundational)
4. Install Proxmox VE on HP DL360 Gen9
5. Validate Proxmox management access
6. Decide and document CloudStack ↔ Proxmox integration model
7. Register hypervisor / compute resources

### Mid-term (Infrastructure)
8. Create CloudStack zones, pods, clusters
9. Define storage pools
10. Implement VLANs
11. Enable inter-VLAN routing
12. Introduce routing protocols (OSPF)

### Advanced (Enterprise / SP)
13. Deploy F5 BIG-IP VE
14. Deploy Aruba EdgeConnect (Silver Peak)
15. Introduce WAN emulation (Netropy)
16. Add monitoring and logging (Zabbix, rsyslog)
17. Security tooling (Nessus)

### Automation & Operations
18. Terraform (infra as code)
19. Ansible (configuration management)
20. CloudStack API usage
21. Cisco API usage
22. Telemetry and observability workflows

## Desired End State
- Proxmox VE running on DL360 Gen9
- CloudStack fully functional with known admin access
- Hypervisors registered and scheduling workloads
- Multi-VLAN environment with routed segmentation
- Simulated LAN-to-WAN and SD-WAN behavior
- Load balancing and traffic engineering
- Monitoring, logging, and security tooling active
- Automation controlling infra changes
- Lab documented to be re-buildable and teachable

## Next Action (Single Focus)
CloudStack admin credential recovery — nothing else until this is resolved.