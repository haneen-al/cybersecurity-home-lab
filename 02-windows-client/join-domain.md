# Joining our Windows 11 Client to our `home.lab` Domain 

## Intro 
Now we have a domain, but what good is it if there are no clients connected to it? In this section, we will join our Windows client to our `home.lab` domain.

## Purpose
Joining the Windows 11 clienty to the `home.lab` domain allows it to become part of the centralized Active Directory (AD) environment. This allows the client to:
- Authenticate users against the centralized AD domain
- Receive and enforce centralized security policies through Group Policy
- Access domain resources based on user permissions
- Be centrally managed by domain administrators
- Communicate with other domain-joined systems using services provided by the domain controller
This way, we can manage the workstation through the same centralized security and administrative infrastructure used for the entire network.

## Implementation + Results

### Step 1 - Static IP and Renaming Server
Before even promoting the server, two things must be ensured: the server has a static IP address, and the server is renamed. 

If we don't create a static IP address, the server will dynamically obtain its IP address through DHCP. Although a DHCP server may assign the same address repeatedly, the address can change when the lease expires or if the client requests a new lease. Clients and domain services need to reliably locate the domain controller, that is why a predictable IP address is important. 

To ensure the IP address is static, we go to the Control Panel --> Network and Internet --> Network and Sharing Center, and click on th Ethernet adapter. By clicking Properties, we can change the content of the Internet Protocol Version 4. Following our topology, we assign a static IP address of `192.168.0.2` within our `/29` subnet. A `/29` subnet provides 8 total addresses, 6 of which are usable. For now, this is enough to support the number of nodes in our network. The default gateway is `192.168.0.1` which is tied to our pfSense VM that acts as the gateway and firewall. The preferred DNS server is set to the server's own IP address, since this Windows server will also host the DNS service used by Active Directory. Of course, the loopback address `127.0.0.1` could also be used. 

![IP Addressing](../screenshots/01-windows-server-ss/static_ip.png)

