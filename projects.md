[Home](index) | [About](about) | [Skills](skills) | [Career Goals](career-goals) | [Resume](resume) 

# Projects

# Cisco Homelab Network

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

## Network Topology

The lab is currently structured as follows:

           Internet
              │
        TP-Link Bridge
              │
        ┌────────────┐
        │   R1       │
        │ Cisco 4300 │
        └──────┬─────┘
               │ 10.0.0.0/30
        ┌──────┴─────┐
        │   R2       │
        │ Cisco 2600 │
        └──────┬─────┘
               │
        ┌──────┴─────┐
        │   SW1      │
        │ Cisco 2960 │
        └───┬───┬────┘
            │   │
          PC   Laptop
                 │
            Raspberry Pi

---

## Purpose of the Lab

This environment allows experimentation with key networking concepts including:

- VLAN segmentation
- Routing between networks
- OSPF routing protocol configuration
- Network troubleshooting techniques
- Infrastructure documentation

Future updates to this project will include configuration examples, troubleshooting scenarios, and verification outputs from the lab environment.

## ICT Capstone Project (Starting)
This portfolio will include reflections on project management, teamwork, technology use, culture awareness, and professional ethics as the project progresses.
