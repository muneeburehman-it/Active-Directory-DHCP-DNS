# **Active Directory Configuration**

1\. Overview



Active Directory Domain Services (AD DS) was deployed on the Windows Server to provide centralized authentication and identity management for the lab environment.



The Windows Server was configured as the Domain Controller for the following domain:



CORP.LOCAL



The Domain Controller hostname is:



DC01



2\. Domain Controller Configuration



The Windows Server was assigned a static IP address because the server provides critical network infrastructure services.



**Parameter**	                                     **Value**

Hostname	                                     DC01

IP Address                                     	     192.168.20.10

Subnet Mask	                                     255.255.255.0

Default Gateway					     192.168.20.1

DNS Server					     192.168.20.10

Domain					             CORP.LOCAL



A static address ensures that clients can consistently locate the Domain Controller and DNS server.



3\. Server Preparation



Before installing Active Directory, the Windows Server was configured with:



A static IPv4 address.

The hostname DC01.

The appropriate default gateway.

DNS configuration.

Network connectivity to the CORP network.



The server was then prepared for installation of Active Directory Domain Services.



4\. Installing Active Directory Domain Services



The Active Directory Domain Services server role was installed on Windows Server.



The installation was performed through:



**Server Manager**

&#x20;       **↓**

**Add Roles and Features**

&#x20;       **↓**

**Active Directory Domain Services**



After the AD DS role was installed, the server was promoted to a Domain Controller.



5\. Creating the Domain



A new Active Directory forest and domain were created using:



CORP.LOCAL



The Windows Server became the first Domain Controller in the lab environment.



The resulting logical structure was:



Forest

└── CORP.LOCAL

&#x20;            └── DC01



6\. Domain Controller Promotion



After installing AD DS, the server was promoted using the Active Directory Domain Services configuration process.



The configuration created the required Active Directory database and supporting services.



After promotion, the server operated as the Domain Controller for:



CORP.LOCAL



The server was then restarted to complete the configuration.





7\. Active Directory Verification



After the restart, the Domain Controller was verified to ensure that Active Directory was operating correctly.



The domain information was confirmed as:



Domain: CORP.LOCAL



The Domain Controller hostname was:



DC01



8\. Domain Authentication



Domain authentication was tested using the domain administrator account.



The domain login format used during testing was:



**Corp\\administrator**



Successful authentication confirmed that the Windows client could communicate with the Active Directory domain.



9\. Client Domain Join



The Windows 10 client was configured to use the Domain Controller as its DNS server.



The client was then joined to:



CORP.LOCAL



The domain join completed successfully.



After restarting the client, domain authentication was tested using the domain account.



10\. Active Directory Verification Flow



The completed process was:



**Windows Server**

&#x20;     **│**

&#x20;     **▼**

**Static IP Configuration**

&#x20;     **│**

&#x20;     **▼**

**Install AD DS**

&#x20;     **│**

&#x20;     **▼**

**Create CORP.LOCAL**

&#x20;     **│**

&#x20;     **▼**

**Promote Server to Domain Controller**

&#x20;     **│**

&#x20;     **▼**

**Restart Server**

&#x20;     **│**

&#x20;     **▼**

**Configure Windows 10 DNS**

&#x20;     **│**

&#x20;     **▼**

**Join Windows 10 to CORP.LOCAL**

&#x20;     **│**

&#x20;     **▼**

**Restart Windows 10**

&#x20;     **│**

&#x20;     **▼**

**Login using domain account**



11\. Result



Active Directory Domain Services was successfully deployed.



The final environment consisted of:



Domain: CORP.LOCAL

Domain Controller: DC01

Domain Controller IP: 192.168.20.10

Windows 10 client successfully joined to the domain

Domain authentication successfully verified



The completed configuration provides centralized Windows domain authentication within the GNS3 lab environment.

