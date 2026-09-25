# **Windows 10 Domain Join**



1\. Overview



The Windows 10 workstation was joined to the Active Directory domain hosted by the Windows Server.



The domain used for this project is:



CORP.LOCAL



The Domain Controller is:



DC01



with the IP address:



192.168.20.10



2\. Prerequisites



Before joining the Windows 10 workstation to the domain, the following requirements were verified:



Windows 10 was connected to the CORP network.

The workstation could communicate with the Domain Controller.

DHCP was functioning correctly.

The workstation received the correct DNS server.

DNS could resolve corp. local.

The Active Directory Domain Controller was operational.



The client needed to use the internal DNS server:



192.168.20.10



rather than relying only on an external DNS server.



3\. Verify Client Network Configuration



The Windows 10 client was configured to obtain its IP configuration through DHCP.



The expected network configuration was:



Network:       192.168.20.0/24

Gateway:       192.168.20.1

DNS Server:    192.168.20.10

Domain:        CORP.LOCAL



Connectivity with the Domain Controller was verified before attempting the domain join.



4\. Test DNS Resolution



The client was tested for internal DNS resolution.



The following domain was successfully resolved:



corp.local



The Domain Controller hostname was also resolved:



dc01.corp.local



Both resolved to:



192.168.20.10



This confirmed that the Windows 10 client could locate the Domain Controller through DNS.



5\. Joining the Domain



The Windows 10 workstation was configured to join the Active Directory domain.



The domain name entered was:



CORP.LOCAL



Windows then requested credentials with permission to join the computer to the domain.



The domain administrator credentials were supplied.



6\. Successful Domain Join



The domain join completed successfully.



Windows displayed confirmation that the computer had joined the domain:



CORP.LOCAL



The workstation was then restarted so that the domain configuration could take effect.



7\. Domain Login



After restarting Windows 10, domain authentication was tested.



The domain login format used was:



corp\\administrator



Successful authentication confirmed that the Windows 10 workstation was communicating with the Active Directory Domain Controller.



8\. Domain Verification



The Windows system information was checked after the restart.



The following domain was displayed:



Domain: CORP.LOCAL



This confirmed that the workstation was successfully joined to the Active Directory environment.



9\. Verification Flow



The complete process was:



**Windows 10**

&#x20;    **│**

&#x20;    **▼**

**Obtain IP through DHCP**

&#x20;    **│**

&#x20;    **▼**

**Use DNS: 192.168.20.10**

&#x20;    **│**

&#x20;    **▼**

**Resolve CORP.LOCAL**

&#x20;    **│**

&#x20;    **▼**

**Locate DC01**

&#x20;    **│**

&#x20;    **▼**

**Join CORP.LOCAL**

&#x20;    **│**

&#x20;    **▼**

**Restart Windows 10**

&#x20;    **│**

&#x20;    **▼**

**Authenticate as:**

**corp\\administrator**

&#x20;    **│**

&#x20;    **▼**

**Domain Join Verified**



10\. Final Result



The Windows 10 workstation was successfully joined to the CORP.LOCAL Active Directory domain.



The final environment was successfully verified with:



DHCP providing client network configuration.

DNS resolving the internal domain.

Domain Controller reachable at 192.168.20.10.

Windows 10 joined to CORP.LOCAL.

Domain authentication working successfully.



This completed the client-side portion of the Active Directory lab.

