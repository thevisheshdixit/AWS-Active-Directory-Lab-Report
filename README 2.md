# AWS Active Directory Domain Join & OU Management Lab

## Overview

This project demonstrates how to configure a Windows client to communicate with an Active Directory Domain Controller hosted on AWS, join the client to the domain, rename the computer, organize it into an Organizational Unit (OU), and verify successful domain communication.

---

## Architecture

- AWS EC2 Windows Server (Domain Controller)
- AWS EC2 Windows Client
- Active Directory Domain Services
- DNS
- Organizational Units

Domain:
lab.local

---

## Objectives

- Verify network connectivity
- Troubleshoot DNS
- Configure correct DNS server
- Join Windows client to Active Directory
- Rename computer
- Move computer into an OU
- Verify successful domain communication

---

## Lab Workflow

1. Verify EC2 instances
2. Test network connectivity
3. Identify DNS issue
4. Verify network configuration
5. Configure Domain Controller as DNS
6. Flush DNS cache
7. Verify DNS resolution
8. Locate Domain Controller
9. Join client to domain
10. Rename computer
11. Restart system
12. Move computer object to IT OU
13. Verify OU placement

---

## Commands Used

```powershell
ping 10.0.0.8

Test-NetConnection 10.0.0.8 -Port 53

ipconfig /all

Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses 10.0.0.8

ipconfig /flushdns

nslookup lab.local

nltest /dsgetdc:lab.local
```

---

## Technologies

- AWS EC2
- Windows Server
- Active Directory Domain Services
- DNS
- PowerShell
- Active Directory Users and Computers

---

## Skills Demonstrated

- Active Directory Administration
- DNS Troubleshooting
- Windows Server Administration
- AWS Infrastructure
- PowerShell
- Network Troubleshooting

---

## Outcome

The Windows client successfully joined the `lab.local` Active Directory domain, was renamed to **IT-1**, moved into the **IT** Organizational Unit, and successfully communicated with the Domain Controller.
