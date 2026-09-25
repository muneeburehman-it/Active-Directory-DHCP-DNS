# **DNS Configuration**



1\. Overview



DNS (Domain Name System) was configured on the Windows Server to provide name resolution for the Active Directory domain.



Because Active Directory depends heavily on DNS, the Domain Controller also operates as the internal DNS server.



The DNS server is:



DC01

192.168.20.10



The Active Directory domain is:



CORP.LOCAL

2\. DNS Server Configuration



The Windows Server was configured with a static IP address:



Parameter	Value

Hostname	DC01

IP Address	192.168.20.10

Subnet Mask	255.255.255.0

Default Gateway	192.168.20.1

DNS Server	192.168.20.10

Domain	CORP.LOCAL



The server uses its own IP address as the preferred DNS server because it hosts the internal DNS service.



3\. DNS Installation



DNS was installed as part of the Active Directory Domain Services deployment.



The DNS service provides name resolution for the internal Windows domain.



The logical relationship is:



Windows 10 Client

&#x20;      │

&#x20;      │ DNS Query

&#x20;      ▼

DC01

192.168.20.10

&#x20;      │

&#x20;      ▼

DNS

&#x20;      │

&#x20;      ▼

CORP.LOCAL

4\. Active Directory DNS Zone



During Active Directory deployment, the DNS namespace associated with the domain was created:



CORP.LOCAL



This allows internal computers to resolve domain-related hostnames.



5\. DNS Records



The following name resolution was tested successfully.



Domain Name

corp.local



Resolved address:



192.168.20.10

Domain Controller

dc01.corp.local



Resolved address:



192.168.20.10



These tests confirmed that DNS was correctly resolving the internal domain and Domain Controller hostname.



6\. DNS Testing



DNS resolution was tested from the Windows client.



A DNS query for:



corp.local



returned:



192.168.20.10



The Domain Controller hostname was also tested:



dc01.corp.local



and successfully resolved to:



192.168.20.10



This verified communication between the client and the internal DNS server.



7\. DNS and Active Directory



DNS is an important component of Active Directory.



The Windows client uses DNS to locate and communicate with services provided by the Domain Controller.



The basic process is:



Windows 10

&#x20;   │

&#x20;   │ DNS request

&#x20;   ▼

192.168.20.10

&#x20;   │

&#x20;   ▼

DNS Server

&#x20;   │

&#x20;   ▼

CORP.LOCAL

&#x20;   │

&#x20;   ▼

Domain Controller



Correct DNS configuration was therefore required before successfully joining the Windows 10 client to the domain.



8\. Client DNS Configuration



The Windows 10 client was configured to obtain its network settings through DHCP.



The DHCP configuration provided the Domain Controller's IP address as the DNS server:



DNS Server:

192.168.20.10



This allowed the client to resolve:



corp.local

dc01.corp.local



and locate the Active Directory domain.



9\. DNS Verification



The following checks were successfully completed:



Test	Result

DNS service installed	Successful

corp.local resolution	Successful

dc01.corp.local resolution	Successful

DNS server reachable	Successful

Client using internal DNS	Successful

Active Directory domain resolution	Successful

10\. Result



DNS was successfully configured as part of the Windows Server infrastructure.



The final DNS environment provides:



Internal name resolution

Active Directory DNS integration

Domain Controller hostname resolution

DNS services for domain clients



The successful DNS configuration allowed the Windows 10 client to locate the Domain Controller and join the CORP.LOCAL domain.

