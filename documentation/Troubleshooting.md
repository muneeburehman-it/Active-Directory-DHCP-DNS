# **Troubleshooting**



1\. Overview



During the implementation of the Active Directory, DNS, and DHCP lab, several configuration and connectivity issues were encountered.



These issues were investigated and resolved during the deployment process.



This document records the main problems, their causes, troubleshooting steps, and final solutions.



2\. DNS Resolution Problem

Problem



Initial DNS testing produced a timeout and the DNS server was not correctly identified.



The query output showed:



DNS request timed out.

Server: Unknown



The DNS query for the internal domain was not initially working as expected.



Investigation



The Domain Controller was checked to verify:



DNS role installation.

Server IP configuration.

DNS service.

DNS server address configured on the client.

Internal DNS records.



The Windows Server was using:



192.168.20.10



as the internal DNS server.



Resolution



The DNS configuration was corrected and the client was configured to use the Domain Controller as its DNS server.



The following records were then successfully resolved:



corp.local

dc01.corp.local



Both resolved to:



192.168.20.10

Result



DNS resolution was successfully restored.



3\. Windows 10 Internet Connectivity Issue

Problem



After configuring the Windows 10 client in the lab, Windows reported:



No Internet

Investigation



The issue was investigated by checking:



Client IP configuration.

Default gateway.

DNS configuration.

Connectivity to the Domain Controller.

DHCP configuration.

Network topology.



The lab's primary objective was internal Active Directory communication rather than unrestricted Internet access.



Resolution



The internal network configuration was verified so that the Windows client could communicate with the Domain Controller and use the internal DNS service.



The client successfully communicated with:



192.168.20.10



and resolved the internal domain.



Result



The Windows client was able to perform the required Active Directory functions even though Internet connectivity was not the primary function of this lab.



4\. DHCP Post-Installation Configuration

Problem



After installing the DHCP Server role, Windows displayed the DHCP post-installation configuration wizard.



Investigation



The DHCP role installation itself had completed, but additional configuration was required before the DHCP server could provide addresses to clients.



Resolution



The DHCP post-installation configuration was completed and the DHCP service was configured for the CORP network.



The client was subsequently able to obtain its network configuration automatically.



Result



DHCP successfully provided network configuration to the Windows 10 client.



5\. Shutdown Event Tracker

Problem



Windows Server displayed the Shutdown Event Tracker after a restart.



The system requested information about the reason for the shutdown/restart.



Investigation



This was identified as a Windows Server administrative feature rather than a network failure.



Resolution



The appropriate restart/shutdown reason information was entered to continue the server configuration process.



Result



The server restarted successfully and continued operating as the Domain Controller.



6\. Domain Join Verification Issue

Problem



Before joining Windows 10 to the domain, it was necessary to ensure that the client could locate the Domain Controller.



Investigation



The following were checked:



Client IP configuration

DNS server

DNS resolution

Domain Controller connectivity



The client needed to use:



192.168.20.10



as its DNS server.



Resolution



After DNS and network connectivity were correctly configured, the Windows 10 workstation was joined to:



CORP.LOCAL

Result



The domain join completed successfully.



The domain was subsequently verified as:



CORP.LOCAL

7\. Troubleshooting Methodology



The troubleshooting process followed a layered approach:



Physical / Virtual Connectivity

&#x20;           │

&#x20;           ▼

&#x20;      IP Configuration

&#x20;           │

&#x20;           ▼

&#x20;       Gateway Test

&#x20;           │

&#x20;           ▼

&#x20;       DNS Testing

&#x20;           │

&#x20;           ▼

&#x20;   Domain Controller Check

&#x20;           │

&#x20;           ▼

&#x20;    Active Directory Check

&#x20;           │

&#x20;           ▼

&#x20;      Domain Join Test

&#x20;           │

&#x20;           ▼

&#x20;    Domain Authentication



This approach helped isolate problems at the network, DNS, DHCP, and Active Directory layers.



8\. Final Verification



After troubleshooting, the following functionality was successfully verified:



Component	Status

Windows Server	Working

Active Directory	Working

Domain Controller	Working

DNS	Working

DHCP	Working

Windows 10 Client	Working

Internal DNS Resolution	Working

Domain Join	Successful

Domain Authentication	Successful

9\. Lessons Learned



This project demonstrated the importance of correct dependency order when deploying a Windows domain environment.



The main dependencies were:



Network Connectivity

&#x20;      ↓

Static Server IP

&#x20;      ↓

DNS

&#x20;      ↓

Active Directory

&#x20;      ↓

DHCP

&#x20;      ↓

Client DNS Configuration

&#x20;      ↓

Domain Join

&#x20;      ↓

Domain Authentication



A correctly configured DNS service is particularly important because Active Directory relies on DNS to locate domain services.



The troubleshooting process also demonstrated the importance of verifying each layer individually rather than changing multiple configurations at the same time.

