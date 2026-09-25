# Active Directory, DHCP & DNS Lab

## 📌 Project Overview

This project demonstrates the deployment of a small Windows-based enterprise network using **GNS3, Windows Server, Windows 10, Active Directory Domain Services (AD DS), DNS, and DHCP**.

The objective was to build a centralized Windows domain environment where client computers can automatically obtain network configuration, resolve internal domain names, and authenticate against an Active Directory Domain Controller.

The lab was designed and tested in GNS3 using a **Windows Server Domain Controller** and a **Windows 10 client**.

---

## 🎯 Objectives

* Deploy a Windows Server Domain Controller
* Install and configure Active Directory Domain Services
* Create the `CORP.LOCAL` Active Directory domain
* Configure internal DNS
* Configure DHCP for automatic IP address assignment
* Connect Windows clients to the domain
* Verify domain authentication and name resolution
* Test communication between the client and Domain Controller
* Document troubleshooting performed during deployment

---

## 🏗️ Network Topology

```text
                    Internet
                       │
                      NAT
                       │
                 Cisco IOSvL2
                  VLAN 20 CORP
                   /          \
                  /            \
        Windows Server       Windows 10
             DC01               Client
        192.168.20.10          DHCP
        AD DS / DNS / DHCP
```

---

## 🌐 Network Information

| Component               | Configuration     |
| ----------------------- | ----------------- |
| VLAN                    | VLAN 20 — CORP    |
| Network                 | `192.168.20.0/24` |
| Default Gateway         | `192.168.20.1`    |
| Domain Controller       | DC01              |
| Server IP               | `192.168.20.10`   |
| Active Directory Domain | `CORP.LOCAL`      |
| DNS Server              | `192.168.20.10`   |
| Client                  | Windows 10        |
| Client Addressing       | DHCP              |

---

## 🖥️ Main Components

### Domain Controller

The Windows Server operates as the central server for the lab.

**Services provided:**

* Active Directory Domain Services
* DNS
* DHCP
* Domain authentication

### Windows 10 Client

The Windows 10 workstation receives its network configuration through DHCP and is joined to the `CORP.LOCAL` domain.

---

## 🔐 Active Directory

The Active Directory domain created for this project is:

```text
CORP.LOCAL
```

The Domain Controller hostname is:

```text
DC01
```

The Windows 10 client was successfully joined to the domain and verified using domain authentication.

---

## 🌍 DNS

DNS was configured on the Domain Controller to provide name resolution for the internal Windows domain.

The following names were tested:

```text
corp.local
dc01.corp.local
```

The domain resolved to:

```text
192.168.20.10
```

---

## 📡 DHCP

DHCP was configured to automatically provide network configuration to Windows clients.

The client received:

* IP address
* Subnet mask
* Default gateway
* DNS server
* Network configuration

This eliminated the need to manually configure the Windows client's network settings.

---

## ✅ Verification

The following tests were successfully completed:

* Windows Server received its static IP configuration
* DNS service was installed and configured
* `corp.local` resolved to `192.168.20.10`
* `dc01.corp.local` resolved correctly
* Windows 10 received an IP address through DHCP
* Windows 10 successfully communicated with the Domain Controller
* Windows 10 successfully joined the `CORP.LOCAL` domain
* Domain authentication was successfully tested

---

## 🛠️ Technologies Used

* GNS3
* Windows Server
* Windows 10
* Cisco IOSvL2
* Active Directory Domain Services
* DNS
* DHCP
* TCP/IP
* VLANs

---

## 📚 Documentation

Detailed documentation for this project is available in the [`documentation`](documentation/) directory.

* [Network Design](documentation/network-design.md)
* [Active Directory Configuration](documentation/active-directory.md)
* [DNS Configuration](documentation/dns-configuration.md)
* [DHCP Configuration](documentation/dhcp-configuration.md)
* [Domain Join](documentation/domain-join.md)
* [Troubleshooting](documentation/troubleshooting.md)

---

## 📸 Screenshots

Project screenshots are available in the [`screenshots`](screenshots/) directory.

The screenshots demonstrate:

* Network topology
* Server IP configuration
* Active Directory configuration
* DNS configuration
* DHCP configuration
* Windows domain join
* Verification and testing

---

## 📌 Project Status

**Status: Completed and Verified ✅**

The complete lab was successfully deployed and tested in GNS3, including Active Directory, DNS, DHCP, Windows 10 domain integration, and connectivity verification.
