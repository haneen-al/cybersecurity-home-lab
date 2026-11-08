# Topology Evolution

## Intro 
This section highlights the topology of the virtualized home lab. 

## Description
This topology shows the transition from the physical connection from the host PC, to the virtualized connections from the pfSense and downstream. The pfSense VM is structured to have 3 virtualized network adapters, `em0`, `em1`, and `em2`. 

`em0` is conceptually the pfSense WAN interface. This interface is configured to use NAT to connect with the Internet through the host PC. NAT effectively takes the interface's private IP address, and translates it into the public IP address my physical network uses to communicate with the Internet. This WAN uses DHCP to assign IP addresses to the `em0` interface from the IP address subnet `192.168.73.128/24`.

`em1` is the virtual LAN that our enterprise devices are a part of. This virtual LAN simulates the internal enterprise network and using the IP address subnet `192.168.0.0/29`. The Windows server, Windows cient, and Ubuntu SOC server all currently are configured with static addresses within this subnet.

`em2` is the external virtual LAN that acts as the attacker network. This network uses a network subnet of 192.168.30.0/24. The Kali Linux pentesting VM will be placed within this network. This VM has not yet been configured.

`em1` and `em2` both operate within a Host-Only network and do not have direct access to the Internet. The pfSense firewall will act as the router and gateway to the Internet. This helps support effective security controls that manage the transmission of authorized packets heading into and out of the internal network.

## Topology

![Topology](../screenshots/03-topologies-ss/Topology-Before-VLANs)

## Things to Note

The following characteristics of this topology will need to be changed/tuned for future implementations:
- The internal LAN subnet is too small, this current subnet was configured to only allow 6 usable addresses for easy configuration, but does not do a good job of reflecting a real internal enterprise network
- Furthermore, as I work towards implementing VLANs within this internal network, it will be important to have more address space available
- Thus, I will change the 192.168.0.0/29 network to have a subnet mask of /24 
- DHCP is not yet configured on the pfSense VM
- Right now, our Windows client and Ubuntu server are configured with static IP addresses
- I plan to automatically allocate these VMs with IP addresses using DHCP configured on the pfSense VM, the Windows server will maintain the same IP address always for discovery.
