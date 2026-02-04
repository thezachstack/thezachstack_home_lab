# Lab as Built

Last updated: 2026-02-04  
Author: thezachstack

This document is the canonical, living "as-built" record for the home lab. It contains hardware inventory, network addressing, virtualization status, current problems, and prioritized tasks.

---

## Summary / Current status
Status: CURRENT STATUS (AS-BUILT, VERIFIED)

- Physical hardware present and reachable.
- CloudStack management server running, but admin credentials currently inaccessible.
- No hypervisors registered to CloudStack yet.
- Flat L2 network (192.168.100.0/24) in place.

---

## Hardware inventory
- HP ProLiant DL360 Gen9
  - Role: target for Proxmox VE installation (no hypervisor installed yet)
  - Rack: 12U rack
  - PDU outlet: documented in INVENTORY.md
- Cisco ISR 2811
  - Role: lab edge/router, basic configuration applied
- Cisco Catalyst 3550
  - Role: aggregation switch, basic configuration applied
- Cisco Aironet 2802i AP
  - Power: AIR-PWRINJ6 inline injector
- Dell OptiPlex workstation
  - OS: Ubuntu 24.04
  - Role: management/admin workstation (SSH, Ansible control)
- Rack and cabling
  - 12U rack; power cabling completed

Reference hardware details and serials: see INVENTORY.md

---

## Network
- VLANs: none (flat L2)
- Addressing: 192.168.100.0/24
- Management host: 192.168.100.X (see INVENTORY.md)
- CloudStack GUI: http://192.168.100.51:8080/client

Planned: implement VLAN segmentation and inter-VLAN routing once hypervisor and switching changes are validated.

---

## Virtualization / CloudStack
- CloudStack Management Server
  - OS: Debian (management server)
  - MariaDB: local, service running (needs verification after reboot)
  - Service: boots cleanly (verify after host reboot)
  - GUI: reachable but login blocked (admin credentials unknown)
- No hypervisors registered (Proxmox target planned)

Important problem (blocking): CloudStack admin credential recovery — this must be resolved before registering hypervisors or creating zones.

---

## Pending tasking (ordered — do not reorder)
### Immediate (BLOCKING)
1. Recover or reset CloudStack admin login (single focus)
   - Backup server (snapshot or disk image)
   - Dump MariaDB cloudstack database
   - Inspect management config and `user` table
   - Attempt CloudStack CLI/API recovery or create a new admin account
   - Document and secure final admin credentials in Vault

2. Verify CloudStack persistence across reboot
   - Confirm cloudstack-management and mariadb are enabled and start on boot

3. Confirm CloudStack DB and config alignment after recovery

### Short-term (Foundational)
4. Install Proxmox VE on HP DL360 Gen9
5. Validate Proxmox management access and networking
6. Decide on CloudStack ↔ Proxmox integration (native driver or use KVM via CloudStack)
7. Register hypervisor/compute resources in CloudStack

### Mid-term (Infrastructure)
8. Create CloudStack zones, pods, clusters
9. Define storage pools (local, NFS, iSCSI)
10. Implement VLANs and switch configs
11. Enable inter-VLAN routing (router/virtual router)
12. Introduce routing protocol (OSPF) for multi-subnet routing

### Advanced (Enterprise / SP)
13. Deploy F5 BIG-IP VE (LBaaS test)
14. Deploy Aruba EdgeConnect (Silver Peak) for SD-WAN tests
15. Add WAN emulation (Netropy)
16. Add monitoring and logging (Zabbix, rsyslog)
17. Add security tooling (Nessus)

### Automation & operations
18. Terraform for infra definition
19. Ansible for configuration management
20. CloudStack API and automation
21. Cisco API / automation (Netmiko, NAPALM, etc.)
22. Telemetry and observability workflows

---

## Desired end state (short)
- Proxmox VE running on DL360 and managed
- CloudStack admin access restored and documented
- Hypervisors registered and workloads schedulable
- Multi-VLAN segmented network with routing
- Observability, backups, and automation in place

---

## Change log
- 2026-02-04 — Initial as-built content added and verified (author: thezachstack)

---

## Next immediate actions (what to run now)
1. On CloudStack host:
   - sudo systemctl status cloudstack-management --no-pager
   - sudo systemctl is-enabled cloudstack-management
   - sudo systemctl status mariadb --no-pager
   - sudo systemctl is-enabled mariadb
   - sudo ss -ltnp | grep 8080
   - sudo journalctl -u cloudstack-management -n 200 --no-pager
   - sudo tail -n 200 /var/log/cloudstack/management/management-server.log

2. From management workstation:
   - curl -I http://192.168.100.51:8080/client

3. If services are up, create a DB dump:
   - sudo mysqldump -u root -p cloud > ~/cloudstack-db-backup-$(date +%F).sql

Document outputs in the issue: #1 [BLOCKER] CloudStack admin credential recovery

---

Notes
- Do not commit secrets, passwords, or DB dumps to this repo. Use GitHub Secrets or external vaults.
- Keep LAB-AS-BUILT.md as the single source of truth for lab state.
