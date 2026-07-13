# AWS Active Directory Lab on EC2

![AWS](https://img.shields.io/badge/AWS-EC2-orange)
![Windows Server](https://img.shields.io/badge/Windows_Server-2025-blue)
![Active Directory](https://img.shields.io/badge/Active_Directory-AD_DS-success)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

## Overview

This project demonstrates how to deploy an **Active Directory Domain Services (AD DS)** environment on **AWS EC2 Windows Server 2025** using a custom **Amazon VPC**.

The lab covers the complete deployment from networking to domain creation and provides the foundation for practicing:

- Active Directory Administration
- DNS
- Organizational Units (OU)
- Domain Users & Groups
- Group Policy
- Domain Join
- Windows Server Administration

---

# Architecture

```
                    Internet
                        │
                        ▼
                Internet Gateway
                        │
                        ▼
                AWS Custom VPC
                (10.0.0.0/24)
                        │
        ┌───────────────┴───────────────┐
        │                               │
        ▼                               ▼
 Windows Server 2025              Windows Client
 Domain Controller                 Domain Member
 (lab.local)                        (Joined)
```

---

# Technologies Used

- AWS EC2
- Amazon VPC
- Internet Gateway
- Route Tables
- Security Groups
- Windows Server 2025
- Active Directory Domain Services
- DNS Server
- RDP
- PowerShell

---

# AWS Infrastructure Setup

## Step 1

Create a **Custom VPC**

```
CIDR

10.0.0.0/24
```

---

## Step 2

Create an **Internet Gateway**

Attach it to the VPC.

---

## Step 3

Create a Public Subnet

Example

```
10.0.0.0/24
```

Enable

- Auto Assign Public IPv4

---

## Step 4

Create Route Table

Add

```
Destination

0.0.0.0/0

Target

Internet Gateway
```

Associate the Route Table with the Public Subnet.

---

## Step 5

Create Security Group

Allow

| Port | Protocol | Purpose |
|-------|----------|----------|
|3389|TCP|Remote Desktop|
|80|TCP|HTTP|
|443|TCP|HTTPS|
|22|TCP|SSH (Optional)|

---

## Step 6

Launch Windows Server EC2

Configuration

- Windows Server 2025
- Public IP Enabled
- Public Subnet
- Security Group
- Key Pair

---

## Step 7

Connect using RDP

Retrieve Administrator Password

```
EC2
→ Connect
→ RDP Client
→ Get Password
```

Login successfully.

---

# Installing Active Directory

## Install AD DS Role

```
Server Manager

↓

Add Roles and Features

↓

Role-based Installation

↓

Active Directory Domain Services
```

---

## Promote Server

```
Promote this server to a Domain Controller
```

Choose

```
Add New Forest
```

Domain

```
lab.local
```

---

## Configure Domain Controller

Enable

- DNS Server
- Global Catalog

Set

- DSRM Password

---

## NetBIOS

Default

```
LAB
```

---

## Database

Keep default locations

```
C:\Windows\NTDS

C:\Windows\SYSVOL
```

---

## Install

Complete the wizard.

Restart Windows Server.

---

# Verification

Open

```
Server Manager

↓

Tools

↓

Active Directory Users and Computers
```

You should see

```
lab.local

│

├── Users

├── Computers

├── Domain Controllers

├── Builtin

├── IT

├── HR

└── Servers
```

---

# Joining Additional Windows EC2 Machines

Launch another Windows EC2 instance.

Requirements

- Same VPC
- Same Route Table
- Same Security Group (or equivalent)
- Same Network

---

## Configure DNS

Preferred DNS

```
Domain Controller Private IP

Example

10.0.0.8
```

---

## Join Domain

```
System

↓

Rename this PC

↓

Change

↓

Domain

↓

lab.local
```

Login

```
LAB\Administrator
```

Restart the machine.

---

## Verify

Open

```
Active Directory Users and Computers
```

The new computer appears under

```
Computers
```

Move it into

```
Servers
```

or

```
IT
```

---

# Skills Demonstrated

- AWS Networking
- Amazon VPC
- Internet Gateway
- Route Tables
- Security Groups
- Windows Server Administration
- Active Directory
- DNS
- Organizational Units
- User Management
- Group Management
- Domain Join
- EC2 Administration
- Remote Desktop
- PowerShell

---

# Future Improvements

- Group Policy Objects (GPO)
- DHCP Server
- File Server
- DFS
- WSUS
- AD Certificate Services
- Additional Domain Controller
- Forest Trust
- VPN Connection
- Bastion Host
- Hybrid AD with Azure

---

# Learning Outcomes

After completing this lab, you will understand how to:

- Design AWS networking
- Configure EC2 networking
- Deploy Active Directory
- Configure DNS
- Create Organizational Units
- Create Users and Groups
- Join Windows Clients to a Domain
- Manage Active Directory from Windows Server

---

# Author

**Vishesh Dixit**

BCA Graduate | AWS | Networking | Windows Server | Active Directory | Cybersecurity

GitHub: https://github.com/thevisheshdixit

LinkedIn: https://linkedin.com/in/thevisheshdixit

---

If you found this project useful, consider giving the repository a Star.
