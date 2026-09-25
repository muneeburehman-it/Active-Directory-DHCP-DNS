# **Network Design**



1\. Overview



The network for this project was designed as a small enterprise environment containing a Windows Server Domain Controller and a Windows 10 client.



The network was implemented in GNS3 using a Cisco IOSvL2 switch. The internal systems were placed in VLAN 20 — CORP.



The Windows Server provides centralized network and directory services, while the Windows 10 client obtains its network configuration through DHCP and joins the Active Directory domain.



2\. Network Topology

&#x20;                        Internet

&#x20;                           │

&#x20;                          NAT

&#x20;                           │

&#x20;                           │

&#x20;                    Cisco IOSvL2

&#x20;                           │

&#x20;                      VLAN 20

&#x20;                        CORP

&#x20;                      /       \\

&#x20;                     /         \\

&#x20;                    /           \\

&#x20;           Windows Server      Windows 10

&#x20;                DC01             Client

&#x20;           192.168.20.10          DHCP

&#x20;                 │

&#x20;         ┌───────┴──────┐

&#x20;         │                  │

&#x20;        DNS                 DHCP

&#x20;         │

&#x20;   Active Directory





3\. VLAN Design

VLAN ID	VLAN Name	Network	Purpose

20	CORP	192.168.20.0/24	Corporate Windows network



The CORP VLAN provides connectivity between the Domain Controller and Windows client.



4\. IP Addressing

Device	Hostname	IP Address	Subnet Mask	Gateway

Windows Server	DC01	192.168.20.10	255.255.255.0	192.168.20.1

Windows 10	Client	DHCP	255.255.255.0	192.168.20.1



The Domain Controller uses a static IP address because it provides infrastructure services such as DNS and Active Directory.



The Windows 10 client uses DHCP for automatic network configuration.



5\. Domain Information

Parameter	Value

Domain Name	CORP.LOCAL

Domain Controller	DC01

Domain Controller IP	192.168.20.10

DNS Server	192.168.20.10



The Windows Server was configured as the Domain Controller for the CORP.LOCAL domain.



6\. Network Services



The Windows Server provides the following services:



Active Directory Domain Services



Active Directory provides centralized identity and authentication for domain-joined Windows computers.



DNS



DNS provides name resolution for the internal domain.



Examples:



corp. local

dc01.corp.local

DHCP



DHCP automatically provides network configuration to client computers.



The DHCP service provides the client with the appropriate:



IP address

Subnet mask

Default gateway

DNS server

Domain information

7\. Client Connectivity



The Windows 10 client is connected to the same CORP network as the Domain Controller.



After receiving its configuration through DHCP, the client was able to communicate with the Domain Controller and resolve internal DNS records.



The client was subsequently joined to:



CORP.LOCAL

8\. Network Verification



The following connectivity and configuration tests were performed:



DNS Resolution



The following domain name was successfully resolved:



corp. local



Result:



192.168.20.10



The Domain Controller hostname was also successfully resolved:



dc01.corp.local

Client Configuration



The Windows 10 client successfully received its network configuration through DHCP.



Domain Connectivity



The Windows 10 client successfully communicated with the Domain Controller.



Domain Join



The Windows 10 client successfully joined the:



CORP.LOCAL



domain.



9\. Design Summary



The final network provides a basic enterprise Windows infrastructure consisting of:



&#x20;                   CORP Network

&#x20;                 192.168.20.0/24

&#x20;                        │

&#x09;		 |

&#x20;                 Cisco IOSvL2

&#x20;                   VLAN 20

&#x20;                  /        \\

&#x20;                 /          \\

&#x20;            DC01            Windows 10

&#x20;       192.168.20.10         DHCP

&#x20;            │

&#x20;      ┌─────┼─────┐

&#x20;      │      │       │

&#x20;     AD      DNS   DHCP



This architecture provides centralized authentication, DNS name resolution, and automatic IP configuration for domain clients.

