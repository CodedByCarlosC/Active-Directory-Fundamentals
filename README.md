# Active-Directory-Fundamentals
Hands-on Active Directory lab covering users, computers, GPOs, authentication, and enterprise domain architecture.
# 🏢 Active Directory Fundamentals – Enterprise Lab

## 📘 Overview

This repository documents my **hands-on learning and administration of Microsoft Active Directory** through a TryHackMe enterprise-style lab environment.

The focus of this project was to understand how **Windows domains are structured, managed, and secured at scale**, while performing real administrative tasks that reflect real-world corporate environments.

Rather than following step-by-step instructions, this project emphasizes **why design and security decisions are made**, how policies affect users and systems, and where common Active Directory risks exist.

---

## 🧠 Core Concepts Covered

- Active Directory Domain Services (AD DS)
- Windows domains and Domain Controllers
- Users, computers, security groups, and OUs
- Delegation of control and least privilege
- Group Policy Objects (GPOs)
- Kerberos vs NetNTLM authentication
- Domain trees, forests, and trust relationships

---

## 🧩 Lab Environment

- **Platform:** TryHackMe  
- **Domain:** `thm.local`  
- **Systems:**  
  - Windows Server (Domain Controller)  
  - Domain-joined Windows clients  
- **Tools Used:**  
  - Active Directory Users and Computers (ADUC)  
  - Group Policy Management  
  - PowerShell  
  - Remote Desktop Protocol (RDP)  

---

## 👤 Users, Computers, and OU Design

I designed and maintained a structured Active Directory environment by:

- Organizing users into department-based OUs
- Creating and removing users to reflect business changes
- Cleaning up unused and deprecated OUs
- Separating machines into:
  - Workstations
  - Servers
  - Domain Controllers

This structure enabled **targeted policy enforcement** and simplified long-term management.

![image](https://github.com/CodedByCarlosC/Active-Directory-Fundamentals/blob/97fc379205c81637ae97d1e0fbec62496a37b391/users.png)
![image](https://github.com/CodedByCarlosC/Active-Directory-Fundamentals/blob/97fc379205c81637ae97d1e0fbec62496a37b391/user%20names.png)

---

## 🔐 Delegation & Least Privilege

To avoid overusing Domain Admin privileges, I implemented **delegation of control** at the OU level.

Tasks included:
- Delegating password reset permissions to IT support users
- Restricting delegated users from broader administrative access
- Validating delegated permissions using PowerShell

This reflects real-world enterprise security practices.

![image](https://github.com/CodedByCarlosC/Active-Directory-Fundamentals/blob/97fc379205c81637ae97d1e0fbec62496a37b391/tasks%20to%20delegate.png)

---

## ⚙️ Group Policy Objects (GPOs)

I created and managed multiple GPOs to enforce security baselines, including:

- Enforcing minimum password length requirements
- Restricting Control Panel access for non-IT users
- Automatically locking screens after inactivity
- Applying policies using OU inheritance and domain-level scope

Policy behavior was validated using test accounts and forced updates with:
```powershell & gpupdate /force `

![image]()

---

🔑 Authentication in Windows Domains

I explored how authentication works within Active Directory:

Kerberos (Default)

Ticket-based authentication using TGTs and TGSs

Centralized validation via the Domain Controller

Secure, scalable authentication for modern domains

NetNTLM (Legacy)

Challenge–response authentication

Retained for backward compatibility

Increased attack surface compared to Kerberos

Understanding both protocols is critical for detecting authentication abuse and lateral movement.

![image]()

---

🌐 Scaling Active Directory

I studied how Active Directory scales in enterprise environments using:

Domain trees for shared namespaces

Forests for multiple namespaces

Trust relationships for controlled cross-domain access

Authentication across domains does not imply authorization; access must always be explicitly granted.

![image]()

---

🛡️ Security Takeaways

Active Directory is a primary attack surface in enterprises

OU and GPO design directly impact security posture

Delegation and least privilege reduce risk

Authentication misconfigurations enable lateral movement

Strong architecture improves detection and response

---

🚀 Next Steps

Additional Active Directory security labs

Authentication and log analysis

SIEM-based monitoring of domain activity

---

📌 Why This Matters

This project demonstrates enterprise Windows administration and security fundamentals, providing hands-on experience relevant to SOC, blue team, and incident response roles.
