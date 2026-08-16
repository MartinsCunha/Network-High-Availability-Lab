# Cisco Network High Availability & ISP Failover Lab

## Overview

This project demonstrates the design, implementation, and validation of a redundant Cisco network in an EVE-NG virtual lab environment.

The main objective was to implement high availability, routing redundancy, and automatic ISP failover while maintaining network connectivity during failure scenarios.

## Lab Environment

- EVE-NG
- Cisco IOS Routers
- Cisco Multilayer Switches
- VPCS
- Two ISP connections

## Technologies Implemented

- OSPF
- ECMP (Equal-Cost Multi-Path)
- HSRP (Hot Standby Router Protocol)
- IP SLA
- Object Tracking
- NAT/PAT
- Cisco CEF
- Static Routes
- Default Routes
- Network Failover
- Network Troubleshooting

## Network Topology

![Network Topology](screenshots/01-topology.png)

The topology consists of redundant routing and switching paths, two ISP connections, and multiple VLANs providing connectivity to end devices.

## Key Implementations

### OSPF and ECMP

OSPF was implemented to provide dynamic routing between the network devices.

Equal-cost paths were established to provide routing redundancy and load sharing.

The routing table and Cisco CEF were used to verify the presence of multiple forwarding paths.

### HSRP

HSRP was implemented at the distribution layer to provide redundant default gateways for the VLANs.

The HSRP configuration allows the distribution switches to provide gateway redundancy while maintaining network availability.

### IP SLA and Object Tracking

IP SLA was configured at the core layer to actively monitor upstream Internet connectivity.

Object Tracking was associated with the IP SLA operation to detect changes in reachability.

When the monitored path becomes unavailable, the tracking state changes accordingly and the routing behavior can react to the failure.

### ISP Failover

The primary ISP path was intentionally disabled to simulate an Internet connectivity failure.

The failure was detected by IP SLA and Object Tracking, while the network maintained connectivity through the redundant path.

## Verification and Troubleshooting

The following commands were used to verify the implementation:

```text
show ip route
show ip cef
show standby brief
show ip sla statistics
show track
ping
traceroute
