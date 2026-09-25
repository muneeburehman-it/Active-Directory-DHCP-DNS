# **DHCP Configuration**

1\. Overview



DHCP (Dynamic Host Configuration Protocol) was configured on the Windows Server to automatically provide network configuration to client computers.



The DHCP service allows Windows clients to obtain their IP configuration without manually assigning an address to each workstation.



The Windows Server operates as the DHCP server for the CORP network.



2\. DHCP Network



The DHCP service operates on:



Network: 192.168.20.0/24

Gateway: 192.168.20.1

DNS Server: 192.168.20.10

Domain: CORP.LOCAL



The Domain Controller has a static address:



192.168.20.10



This address is reserved for the Windows Server and infrastructure services.



3\. DHCP Server



**Parameter				Value**

DHCP Server				DC01

DHCP Server IP				192.168.20.10

Network					192.168.20.0/24

Subnet Mask				255.255.255.0

Default Gateway				192.168.20.1

DNS Server				192.168.20.10

DNS Domain				CORP.LOCAL



4\. DHCP Installation



The DHCP Server role was installed on the Windows Server.



The installation was performed through:



**Server Manager**

&#x20;       **↓**

**Add Roles and Features**

&#x20;       **↓**

**DHCP Server**



After installation, the DHCP server was configured for the CORP network.



5\. DHCP Scope



A DHCP scope was configured for the 192.168.20.0/24 network.



The scope provides addresses to client computers on the CORP network.



The DHCP configuration supplies the client with:



IPv4 address

Subnet mask

Default gateway

DNS server

DNS domain information

6\. DHCP Options



The important DHCP options used by the client are:



**DHCP Option				Purpose	Value**

003					Default Gateway	192.168.20.1

006					DNS Server	192.168.20.10

015					DNS Domain Name	CORP.LOCAL



These options ensure that the client receives the information required to communicate with the internal network and Active Directory.



7\. Windows 10 DHCP Client



The Windows 10 workstation was configured to obtain its IPv4 configuration automatically.



The client therefore does not require a manually assigned IP address.



The process is:



**Windows 10**

&#x20;    **│**

&#x20;    **│ DHCP Discover**

&#x20;    **▼**

**DHCP Server**

**DC01**

&#x20;    **│**

&#x20;    **│ DHCP Offer**

&#x20;    **▼**

**Windows 10**

&#x20;    **│**

&#x20;    **▼**

**IP Configuration**



8\. Client Configuration



After DHCP was enabled on Windows 10, the client received its network configuration automatically.



The client was configured with:



IP Address:	 DHCP assigned

Subnet Mask:	 255.255.255.0

Gateway:	 192.168.20.1

DNS:		 192.168.20.10

Domain:		 CORP.LOCAL



9\. DHCP Verification



The DHCP configuration was verified by checking the Windows client's network configuration.



The client successfully obtained an IP address from the DHCP server.



The assigned configuration allowed the client to:



Communicate with the Domain Controller.

Resolve internal DNS names.

Access the CORP.LOCAL domain.

Successfully join the Active Directory domain.

10\. DHCP and Active Directory



DHCP and DNS work together with Active Directory in this lab.



The overall process is:



&#x20;             Windows 10

&#x20;                  │

&#x20;                  │ DHCP

&#x20;                  ▼

&#x20;                DC01

&#x20;                  │

&#x20;       ┌──────────┴──────────┐

&#x20;       │                  		    │

&#x20;      DHCP               	   DNS

&#x20;       │                	        │

&#x20;       ▼                          ▼

Network Configuration          CORP.LOCAL

&#x20;                                   │

&#x20;                                   ▼

&#x20;                            Active Directory





The client first obtains its network configuration through DHCP and then uses the supplied DNS server to locate the Active Directory domain.



11\. Result



The DHCP service was successfully configured on the Windows Server.



The Windows 10 client successfully obtained its network configuration automatically and was subsequently able to communicate with the Domain Controller and join the CORP.LOCAL domain.



The completed DHCP environment provides centralized and automatic IP configuration for clients on the CORP network.

