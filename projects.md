<nav class="page-nav">
  <a href="index">Home</a>
  <a href="about">About</a>
  <a href="skills">Skills</a>
  <a class="active" href="projects">Projects</a>
  <a href="packet-tracer">Packet Tracer</a>
  <a href="career-goals">Career Goals</a>
  <a href="resume">Resume</a>
  <a href="cover-letter">Cover Letter</a>
</nav>

# Projects

# Cisco Homelab Network
<div style="text-align:center;">
  <img src="assets/images/homelab-banner.jpg" alt="Home Lab Hardware" class="project-image">
</div>

A physical Cisco networking lab used to practice routing, switching, OSPF design, and network troubleshooting 
using enterprise hardware.
## Overview

This project documents the development of a personal Cisco networking lab used to practice real-world networking concepts and troubleshooting techniques.

The lab environment allows experimentation with routing, switching, VLAN segmentation, and network troubleshooting using physical Cisco hardware. It complements my formal networking studies and CCNA preparation by providing hands-on experience configuring and diagnosing network infrastructure.

---

## Lab Hardware

The current lab environment includes the following devices:

- Cisco 4300 Series Router (R1)
- Cisco 2600 Series Router (R2)
- Cisco Catalyst 2960 Switch (SW1)
- Raspberry Pi running Linux
- Laptop and PC client devices
- TP-Link bridge providing connectivity to the home network

This setup allows simulation of a small routed network with multiple segments and devices.

---

The lab is currently structured as follows:

## Network Topology

<div style="text-align:center;">
<img src="assets/images/homelab-topology.png" alt="Homelab Network Topology" class="diagram-image">
</div>

This diagram shows the current logical topology of my Cisco homelab, including the edge connection to the home network, the OSPF Area 0 transit network between routers, and the LAN segment behind R2 used for client devices and experimentation.

## IP Addressing Plan (Current)

### Edge / Internet Network (192.168.0.0/24)

| Device | Interface | IP Address | Purpose |
|---|---|---:|---|
| TP-Link Gateway | — | 192.168.0.1/24 | Default gateway to Internet |
| R1 (Cisco 4300) | G0/0/0 | 192.168.0.2/24 | Outside / edge interface |

**Routing**
- R1 has a static default route pointing to **192.168.0.1**.

---

### OSPF Area 0 — Transit Network (10.0.0.0/30)

| Device | Interface | IP Address | Role |
|---|---|---:|---|
| R1 (Cisco 4300) | G0/0/1 | 10.0.0.1/30 | Area 0 backbone |
| R2 (Cisco 2600) | F0/0 | 10.0.0.2/30 | Area 0 backbone |

**Purpose**
- Router adjacency and backbone transit between R1 and R2.

---

### OSPF Area 1 — LAN Network (10.0.1.0/24)

| Device | Interface | IP Address | Notes |
|---|---|---:|---|
| R2 (Cisco 2600) | F0/1 | 10.0.1.253/24 | LAN default gateway |
| SW1 (Cisco 2960) | VLAN 99 | 10.0.1.254/24 | Switch management SVI |

**OSPF Note**
- The LAN interface on R2 is advertised into OSPF but set as **passive** (no neighbor formation on the LAN).

---

### Loopbacks (Router IDs)

| Device | Interface | IP Address | Purpose |
|---|---|---:|---|
| R1 | Loopback0 | 1.1.1.1/32 | OSPF Router ID |
| R2 | Loopback0 | 2.2.2.2/32 | OSPF Router ID |

---

## OSPF Design Summary

| Area | Network | Devices |
|---|---|---|
| Area 0 | 10.0.0.0/30 | R1 ↔ R2 (transit) |
| Area 1 | 10.0.1.0/24 | LAN behind R2 |

- **R2 functions as the ABR** (Area Border Router).
- R2 learns **0.0.0.0/0** via OSPF from R1.

---

## Topology Diagram (Logical)

```
              Internet
                 |
       TP-Link Gateway (192.168.0.1/24)
                 |
        R1 G0/0/0 (192.168.0.2/24)
                 |
    OSPF Area 0: 10.0.0.0/30 (Transit)
       R1 G0/0/1 (10.0.0.1) ---- R2 F0/0 (10.0.0.2)
                 |
            R2 (ABR)
            R2 F0/1 (10.0.1.253/24)
                 |
    OSPF Area 1: 10.0.1.0/24 (LAN)
                 |
     SW1 VLAN 99 SVI (10.0.1.254/24)
                 |
   Clients PC/Laptops/RaspberryPi
```
       
## Purpose of the Lab

This environment is used to practice and document core networking concepts including:

- VLAN segmentation
- Routing between networks
- OSPF routing protocol configuration
- Network troubleshooting techniques
- Infrastructure documentation

Future updates to this project will include configuration examples, troubleshooting scenarios, and verification outputs from the lab environment.

## Capstone Project – CSC3600

## Capstone Project Reflection

CareShield AI – AI-Assisted Case Note Documentation System

During my capstone project, I worked as part of a team to design and develop CareShield AI, a proof-of-concept system created to support aged care and NDIS workers with case note documentation. The system was designed to reduce administrative workload by allowing workers to enter information through voice or text, which could then be processed into structured case notes.

The project combined several technologies, including speech-to-text processing, translation, and AI-assisted text generation. The aim was to improve the consistency, completeness, and efficiency of documentation while considering the privacy and professional responsibilities involved in handling sensitive client information.

## My Role

My role in the project involved contributing to project planning, system analysis, documentation, risk identification, and team coordination. I also supported the development process by helping analyse requirements, understand how the system components connected, and consider how the solution could be presented clearly to a client or stakeholder audience.

Although my main career direction is network engineering, this project gave me valuable experience working within a structured ICT project environment. It helped me better understand how software, AI tools, databases, and user-facing systems can be combined to solve a real-world business problem.

## Key Contributions
Contributed to project planning and requirement analysis.
Assisted with documentation and project reporting.
Helped identify project risks, including workload, team participation, technical complexity, and privacy concerns.
Supported team communication and coordination during the project.
Contributed to the presentation of the final proof-of-concept system.
Reflected on ethical and privacy considerations related to sensitive aged care and NDIS documentation.
Key Learnings

Through this project, I developed a stronger understanding of how ICT projects are planned, managed, and delivered in a team environment. The project showed me that successful ICT work depends not only on technical development, but also on communication, documentation, accountability, and ethical decision-making.

I also gained insight into the importance of privacy, security, and responsible AI use when working with sensitive information. Since CareShield AI involved case notes and personal client information, it was important to consider how data should be handled, stored, and protected.

## Reflection on Career Concepts

The CareShield AI project was outside my main technical focus of network engineering, but it still strengthened skills that are highly relevant to my future career. These included requirements analysis, technical documentation, teamwork, communication, risk awareness, and professional responsibility.

The project also reinforced the importance of reliable ICT infrastructure. Systems like CareShield AI depend on secure networks, stable backend services, protected databases, and dependable access for users. This helped me connect the project back to my interest in network engineering, where reliable infrastructure plays a key role in supporting real-world applications.

## Career Goals and Action Plan

This capstone project confirmed that my primary career goal remains focused on network engineering and infrastructure. While CareShield AI was centred on AI-assisted documentation, the experience helped me understand how broader ICT systems rely on strong technical foundations, including secure connectivity, system reliability, and effective documentation.

My short-term goal is to complete my Bachelor of Information Technology with a focus on Network Engineering, continue developing hands-on skills through my Cisco homelab, and work toward completing the CCNA certification.

My mid-term goal is to gain experience in a junior network engineer, network administrator, or infrastructure support role, where I can apply my technical knowledge in a professional environment.

My long-term goal is to progress into a network engineering or infrastructure engineering position, contributing to the design, implementation, and troubleshooting of reliable network systems.

The capstone project helped strengthen my confidence in working on structured ICT projects and reinforced the value of communication, accountability, documentation, and ethical practice in professional technology environments.


