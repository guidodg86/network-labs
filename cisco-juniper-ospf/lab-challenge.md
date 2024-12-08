# Cisco and Juniper - OSPF

## Diagram
<img src="./cisco-juniper-ospf-diagram.png" alt="diagram"/>

## Topology description

### Hosts subnets

Topology supports four hosts subnets:

- VLAN 10 - 10.10.0.0/24
- VLAN 20 - 10.20.0.0/24
- VLAN 30 - 10.30.0.0/24
- VLAN 40 - 10.40.0.0/24

### Loopbacks
Each router has loopback that matches number, as following:
- R1 = 1.1.1.1/24
- R2 = 2.2.2.2/24
- R3 = 3.3.3.3/24

These loopbacks must be advertise into OSPF.
For example in VLAN 10, virtual IP is 10.10.0.1. R2 has 10.10.0.2 and R3 has 10.10.0.3. 

### OSPF
OSPF is configured the three routers. R1 is ABR with backbone area, R2 and R1 belong to area 25

### VRRP
Each router has 4 subinterfaces on each host vlan. First IP corresponds to the virtual VRRP ip, R2 has second IP on the subnet and R3 has third IP on the subnet

### DCHP
R1 acts as DHCP server for the four vlans. R1 and R2 must have DCHP relay feature configured.
Default route must be included on the DHCP information

### LACP
Connection between SW1 and SW2 must be a two interfaces connection bonded in a LACP aggregation link

## Validating procedure
1. Hosts must be able to ping loopbacks of the routers
2. Uplinks of switches must be disabled to test redundancy
3. Switches port-channel must be disabled to test redundancy
