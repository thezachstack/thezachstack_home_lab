
Welcome to **thezachstack**, where skills... AND switches... are always STACKED for success!

This is a collaborative home lab and systems research environment for studying, building, breaking, and rebuilding modern enterprise and service-provider infrastructure.

While the lab is rooted in my personal work and research, this is NOT a solo effort! The project is designed to grow over time with contributions from other engineers, students, and collaborators who share an interest in infrastructure, automation, and applied computer science.

This lab serves three purposes:
1. Hands-on systems and network engineering practice  
2. A sandbox for automation, virtualization, and orchestration  
3. A research-backed environment aligned with doctoral-level computer science study  

Everything here is designed to be reproducible, documented, and intentionally layered—from physical hardware up through control planes and automation.

---

## Lab Philosophy

- **Build it for real**: Prefer real hardware where feasible, virtualize where it makes sense.
- **Document everything**: If it isn’t written down, it didn’t happen.
- **Break things on purpose**: Failure modes are first-class learning objectives.
- **Theory meets practice**: Architectural decisions are informed by computer science theory, not just vendor documentation.
- **Collaboration over isolation**: Good systems are built and improved through shared effort and peer review.

---

## Physical Infrastructure

- **Rack**
  - 12U open-frame rack
  - Rack-mounted PDU
  - Structured power and network cabling

- **Compute**
  - HP ProLiant DL360 Gen9 (virtualization host)
  - Dell OptiPlex workstation (Ubuntu daily driver)

- **Networking**
  - Cisco ISR router
  - Cisco Catalyst switch
  - Cisco Aironet access point (PoE)
  - Enterprise-grade cabling and labeling

---

## Virtualization & Core Platforms

- **Proxmox VE**
  - Primary hypervisor
  - VM and container workloads
  - Network segmentation and bridge design

- **Apache CloudStack**
  - Infrastructure orchestration and management
  - Multi-tenant concepts
  - Control-plane experimentation

- **Linux**
  - Debian / Ubuntu-based systems
  - systemd, networking, storage, and services

---

## Networking & Traffic Engineering

- VLANs and Layer 2 segmentation  
- Layer 3 routing and inter-VLAN routing  
- LAN-to-WAN simulation  
- Wireless infrastructure integration  
- Planned SD-WAN and traffic optimization experiments  

---

## Automation & Programmability (In Progress)

- Python for network automation
- Bash scripting for system tasks
- REST APIs and service interaction
- Planned integrations:
  - Ansible
  - Terraform
  - NETCONF / RESTCONF
  - Vendor APIs

---

## Monitoring, Services & Tooling (Planned / Partial)

- DNS services (BIND)
- Web-based system management
- Centralized logging
- Metrics and monitoring
- Vulnerability scanning
- Network performance emulation

---

## Documentation Structure

This repository will include contributions from multiple authors and will contain:
- Architecture diagrams
- Build notes and design decisions
- Configuration snippets
- Failure analysis and recovery notes
- Research-aligned reflections (where appropriate)

Nothing here is “magic.” If something works, there will be a documented explanation of *why*.

---

## Intended Outcomes

- Deepen practical understanding of enterprise and service-provider systems
- Bridge computer science theory with operational reality
- Build a shared reference platform for automation and research projects
- Create artifacts that others can learn from, critique, and extend

---

## About This Project

This lab is led by a doctoral student in computer science with a professional background in government contracting and systems engineering, but it is intentionally structured to support **multiple contributors** over time.

---

## Status

🚧 Actively evolving.  
Expect rough edges, refactors, and occasional chaos.

That’s the point.
