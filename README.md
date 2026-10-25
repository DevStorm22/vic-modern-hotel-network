# Vic Modern Hotel — Enterprise Network Design

A hands-on enterprise networking project designed and simulated using **Cisco Packet Tracer**. This project implements a multi-floor hotel network with departmental VLANs, inter-router serial connectivity, OSPF dynamic routing, DHCP, wireless access, SSH remote management, and switch port security.

## Project Overview

Vic Modern Hotel operates across three floors, each containing different departments with specific networking requirements. The objective is to design and implement a reliable, segmented, and interconnected network that allows authorized devices across all departments and floors to communicate.

The network uses three routers located in the IT server room, one switch per floor, eight departmental VLANs, and dedicated IPv4 subnets. OSPF provides dynamic route advertisement between routers, while each router provides DHCP services for its assigned networks.

## Objectives

- Design a network for all three floors of the hotel.
- Connect three routers using serial DCE links.
- Implement eight departmental VLANs with separate IPv4 subnets.
- Configure inter-VLAN routing and OSPF dynamic routing.
- Configure DHCP services on the respective routers.
- Provide wireless connectivity for laptops and mobile devices.
- Connect a printer in each department.
- Enable SSH remote management on all routers.
- Configure sticky MAC address port security on the IT switch.
- Verify end-to-end connectivity across departments and floors.

## Network Requirements

| Requirement | Implementation |
|---|---|
| Simulation tool | Cisco Packet Tracer |
| Floors | 3 |
| Routers | 3 |
| Access switches | 1 per floor |
| Departments | 8 |
| Network segmentation | Separate VLAN per department |
| Inter-router connectivity | Serial DCE links |
| Routing protocol | OSPF |
| IP address assignment | DHCP |
| Wireless access | Laptops and mobile devices |
| Remote management | SSH on all routers |
| Port security | Sticky MAC with shutdown violation mode |

## Departmental VLAN and IP Addressing Plan

### First Floor

| Department | VLAN | Network | Default Gateway |
|---|---:|---|---|
| Reception | 80 | `192.168.8.0/24` | `192.168.8.1` |
| Store | 70 | `192.168.7.0/24` | `192.168.7.1` |
| Logistics | 60 | `192.168.6.0/24` | `192.168.6.1` |

### Second Floor

| Department | VLAN | Network | Default Gateway |
|---|---:|---|---|
| Finance | 50 | `192.168.5.0/24` | `192.168.5.1` |
| HR | 40 | `192.168.4.0/24` | `192.168.4.1` |
| Sales/Marketing | 30 | `192.168.3.0/24` | `192.168.3.1` |

### Third Floor

| Department | VLAN | Network | Default Gateway |
|---|---:|---|---|
| Admin | 20 | `192.168.2.0/24` | `192.168.2.1` |
| IT | 10 | `192.168.1.0/24` | `192.168.1.1` |

*Default gateways are proposed as the first usable address in each subnet and must match the final router configuration.*

## Inter-Router Network Addressing

The routers will use the following point-to-point IPv4 networks:

| Link Network | Subnet Mask | Usable Addresses |
|---|---|---|
| `10.10.10.0/30` | `255.255.255.252` | `10.10.10.1–10.10.10.2` |
| `10.10.10.4/30` | `255.255.255.252` | `10.10.10.5–10.10.10.6` |
| `10.10.10.8/30` | `255.255.255.252` | `10.10.10.9–10.10.10.10` |

These subnets provide point-to-point addressing for the inter-router links. The final topology and interface assignments will determine which addresses are assigned to each router.

## Routing and Network Services

### OSPF Dynamic Routing

OSPF will advertise the departmental and inter-router networks between the three routers, allowing devices on different floors to communicate through dynamically learned routes.

### DHCP

Each router will provide DHCP services for its assigned departmental networks. DHCP pools will specify the correct network, subnet mask, and default gateway, with reserved addresses excluded where necessary.

### Wireless Connectivity

Wireless access will be provided on all floors so that laptops and mobile devices can connect to the appropriate departmental network.

### SSH Remote Management

SSH will be configured on all routers to provide authenticated, encrypted remote CLI access. The IT Test-PC will be used to verify remote login.

### Switch Port Security

The IT switch port `Fa0/1` will be configured to allow only the IT Test-PC using sticky MAC address learning and a violation mode of `shutdown`.

## Project File

- `vic-modern-hotel-network.pkt` — Editable Cisco Packet Tracer simulation.

## Demonstration Video

*Add the link to the project demonstration video here.*

The video will demonstrate the topology, VLANs, serial links, OSPF routing, DHCP address assignment, wireless access, SSH remote login, port security, and connectivity tests.

## Testing and Verification

The completed network will be tested for:

- Correct VLAN creation and port assignments.
- Serial interface connectivity between routers.
- OSPF neighbor adjacency and route advertisement.
- Automatic DHCP address allocation.
- Communication between devices on different VLANs and floors.
- Wireless client connectivity.
- SSH login to all three routers from the IT Test-PC.
- Sticky MAC learning and port-security violation behavior on IT switch `Fa0/1`.

Actual verification results will be recorded after testing in Packet Tracer.

## Expected Outcome

The completed simulation should provide interconnected departmental networks across all three hotel floors, with dynamic routing, automatic IP addressing, wireless access, secure remote router management, and restricted access to the designated IT switch port.

## Learning Outcomes

This project provides practical experience in enterprise network design, VLAN segmentation, serial WAN links, OSPF, DHCP, wireless networking, SSH, switch port security, and end-to-end network troubleshooting.

## Disclaimer

This project is intended for educational purposes and networking skills practice in a simulated environment.
