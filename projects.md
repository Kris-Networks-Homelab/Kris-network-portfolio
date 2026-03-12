[Home](index) | [About](about) | [Skills](skills) | [Projects](projects) | [Career Goals](career-goals) | [Resume](resume) | [Cover Letter](cover-letter) 

# Projects

# Cisco Homelab Network
<div style="text-align:center;">
<img src="assets/images/homelab-banner.jpg" alt="Home Lab Hardware" width="700">
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
<img src="assets/images/homelab-topology.png" alt="Homelab Network Topology" style="width:900px;">
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

## Capstone Project – CSC3600 (Please ignore this section unless marking it)

## Capstone Project Reflection

During my capstone project, I worked as part of a team to design and develop an AI-assisted language processing system capable of recognising spoken input, translating it into English, and classifying the emotional tone of the speech. The system integrates speech recognition, translation technologies, and machine learning models to analyse and interpret spoken communication.

My role in the project involved contributing to the system design, analysing technical requirements, and assisting with the implementation and testing of different components of the solution. The project required collaboration with team members to plan tasks, manage risks, and ensure that different parts of the system worked together effectively.

Through this experience, I gained a deeper understanding of how multiple technologies can be integrated into a single system to solve complex problems. The project also strengthened my ability to analyse technical problems, communicate ideas within a team environment, and manage project tasks within a structured development process.

## Reflection on Career Concepts

The capstone project provided valuable insight into how real-world ICT projects are planned and executed. Working on a complex system highlighted the importance of teamwork, communication, and structured project management when developing technology solutions.

One of the key lessons I gained from the capstone experience is that successful ICT projects require more than technical knowledge. Collaboration, documentation, and the ability to break down complex problems into manageable tasks are equally important. These skills are essential in professional ICT environments where projects often involve multiple stakeholders and interdisciplinary teams.

## Career Goals and Action Plan

This capstone project has reinforced that I am not interested in any of the areas that were part of the project and I shall continue with my original interest, and major of Network Engineering.
I will continue to complete my degree in Network Engineering and look to complete my CCNA in the near future.


