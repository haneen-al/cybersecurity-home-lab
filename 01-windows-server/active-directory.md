## Setting up AD DC on the Windows Server 

### Intro 
Upon opening the Windows Server VM for the first time, we are taken to GUI for the Windows Admin Center. We need to make this server the AC DC, however, it doesn not become an Active Directory Domain Controller until it is promoted. This is our goal.

### Reason
The reasons for turning this server into our AC DC are listed below:
- Runs administrative domain services for any device under its domain
- Acts as a central security authority and database for the network
- Verifies user identities (authentication)
- Grants/denies access to network resources like files and printers (authorization)
As one could imagine, a Windows server acting as an AC DC is essential to any enterprise network.

### How it was done

#### Static IP and Renaming Server
Before evening promoting the server, two things must be ensured: the server has a static IP address, and the server is renamed. 

If we don't create a static IP address, the server will dynamically receive its IP address from some DHCP server. The issue is that this dynamic IP address can and will change, whether the lease for the current IP address runs out, or the server is restarted. Without a static IP address, clients under this soon-to-be domain controller will not be able to find it, leading to unresponsive clients for users. 

To ensure the IP address is static, we go to the Control Panel --> Network and Internet --> Network and Sharing Center, and click on th Ethernet adapter. By clicking Properties, we can change the content of the Internet Protocol Version 4. Following our topology, we assign a static IP address of 192.168.0.2 in our /29 subnet which allows for 8 addresses. The default gateway is 192.168.0.1 which is tied to our pfSense VM that acts as the gateway, firewall, and Layer 3 switch. The preferred DNS server is set to the servers IP address, since this Windows server is also acting as the DNS server for this network. Please note that the loopback address 127.0.0.1 would also work here. 



