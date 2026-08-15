# 🖥️ Windows Server 2019 Administration & PowerShell

![Windows Server](https://img.shields.io/badge/Windows%20Server-2019-blue)
![PowerShell](https://img.shields.io/badge/PowerShell-Administration-blue)
![IIS](https://img.shields.io/badge/IIS-Web%20Server-lightgrey)
![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-red)

## 📌 Project Overview

This project demonstrates hands-on **Windows Server 2019 administration, PowerShell configuration, network management, and server role management** within a virtualized lab environment.

The project focused on preparing and managing a Windows Server system through both PowerShell and Windows Server management tools. Tasks included network discovery, static IP configuration, server renaming, Windows Update configuration, system restart, IIS deployment, role validation, and IIS removal.

From a cybersecurity perspective, this project demonstrates foundational infrastructure concepts that support secure system administration, including **configuration management, patch management, attack-surface reduction, least functionality, and configuration validation**.

---

# 🎯 Project Objectives

The primary objectives of this project were to:

- Analyze the server's existing network configuration
- Configure a static IPv4 address
- Configure the server's default gateway and network prefix
- Rename the Windows Server system
- Manage Windows Update behavior
- Restart the server and validate configuration changes
- Install the IIS Web Server role
- Verify successful role installation
- Remove unnecessary server functionality
- Document configuration changes and validation results

---

# 🏗️ Lab Environment

| Component | Details |
|---|---|
| **Operating System** | Windows Server 2019 |
| **Environment** | Virtualized Lab |
| **Administration** | PowerShell / Server Manager |
| **Web Server** | IIS |
| **Networking** | IPv4 / TCP-IP |
| **Primary Focus** | Windows Server Administration |
| **Security Focus** | Configuration Management & Attack Surface Reduction |

---

# 🧰 Technologies & Tools

### Operating System
- Windows Server 2019

### Administration
- Microsoft PowerShell
- Server Manager
- Windows `sconfig`

### Networking
- IPv4
- TCP/IP
- IP configuration
- Default gateway configuration

### Server Roles
- Internet Information Services (IIS)

### Virtualization
- Virtualized Windows Server lab environment

---

# 🔧 Project Workflow

Network Discovery
       │
       ▼
IP Configuration
       │
       ▼
Static IP Assignment
       │
       ▼
Server Renaming
       │
       ▼
Windows Update Configuration
       │
       ▼
System Restart
       │
       ▼
IIS Installation
       │
       ▼
IIS Validation
       │
       ▼
IIS Removal
       │
       ▼
Final Validation


---

# 1️⃣ Network Discovery

Before making configuration changes, the existing network configuration was reviewed to establish a baseline.

## Get-NetIPAddress

```powershell
Get-NetIPAddress
```

`Get-NetIPAddress` was used to identify existing IP addresses, interface indexes, address families, and prefix lengths.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/7c6c0d5c-862c-4f86-b2aa-2e3a8aee1f5b" />




### Why This Matters

Establishing a configuration baseline before making changes helps administrators understand the existing system state and provides a reference for validating changes later.

---

# 2️⃣ Review Network Configuration

The server's current network configuration was reviewed using:

```powershell
Get-NetIPConfiguration
```

This provided information about the server's network interface, IP configuration, and default gateway.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/2a8665a5-a0b0-438e-b03c-8b86a36dcfb5" />


### Administrative Value

PowerShell provides a fast way to collect network information without navigating through multiple graphical configuration menus.

This approach also provides a foundation for automating system discovery and configuration.

---

# 3️⃣ Configure a Static IPv4 Address

A static IPv4 configuration was assigned using PowerShell:

powershell
New-NetIPAddress -IPAddress 192.168.50.5 -InterfaceIndex 13 -PrefixLength 24 -DefaultGateway 192.168.50.2


The command configured:

| Parameter         | Purpose                          |
| ----------------- | -------------------------------- |
| `-IPAddress`      | Assigns the IPv4 address         |
| `-InterfaceIndex` | Identifies the network interface |
| `-PrefixLength`   | Defines the network prefix       |
| `-DefaultGateway` | Defines the default gateway      |

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/4098a9d2-5d08-4244-a04a-400f7df7b005" />




> **Lab Note:** The IP address and gateway documented above were used within the lab environment and should not be treated as production network settings.

### 🔐 Security Relevance

Understanding a server's network configuration is important when evaluating network exposure, firewall rules, routing, and communication with other systems.

---

# 4️⃣ Rename the Windows Server

The server name was changed using PowerShell:

```powershell
Rename-Computer -NewName "NewPCName" -Force -PassThru
```

The `-PassThru` parameter was used to return information about the resulting configuration.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/50bb4c0a-352b-4bd5-9237-43b165adcd19" />




### Why This Matters

Consistent server naming is important for:

* Asset identification
* System administration
* Monitoring
* Logging
* Troubleshooting
* Security investigations

Proper naming conventions become increasingly important as the number of managed systems grows.

---

# 5️⃣ Configure Windows Update

The Windows Server `sconfig` utility was used to modify Windows Update behavior.

powershell
'sconfig'

The update configuration was changed from automatic updates to manual updates within the lab environment.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/704c1d61-d91d-4194-8427-e4dc156d68b6" />



---

# 6️⃣ Validate Windows Update Configuration

The resulting configuration was reviewed to verify that the change was successfully applied.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/5a073f57-db22-415a-af94-ae95ca8ad2d6" />



## 🔐 Security Consideration

Patch management is an important component of vulnerability management.

While manual updates can provide administrators with greater control over maintenance timing, production environments require a reliable process for ensuring that critical security updates are not delayed.

A production implementation should include:

* Centralized patch management
* Defined maintenance windows
* Patch compliance monitoring
* Vulnerability scanning
* Change management
* Security update prioritization

---

# 7️⃣ Restart the Server

The server was restarted after configuration changes:

```powershell
Restart-Computer
```
<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/ec83b187-811c-4a98-bc6c-af3c12d5cba2" />




The restart provided an opportunity to verify that the server could successfully return to an operational state after configuration changes.

---

# 🌐 IIS Web Server Management

## 8️⃣ Install IIS

The **Internet Information Services (IIS)** Web Server role was installed using Windows Server's Server Manager.

The installation workflow was:

Server Manager
      ↓
Manage
      ↓
Add Roles and Features
      ↓
Web Server (IIS)

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/c61cb7c6-d8e3-4c95-af47-6c579a847b0b" />

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/a4358ce0-c5c5-4c71-b80f-4e4477cea2e1" />


### Why IIS?

IIS is a common Windows Server role used to host web applications and services.

Understanding how server roles are deployed and removed is useful for both system administration and cybersecurity because every enabled service can potentially increase a system's attack surface.

---

# 9️⃣ Validate IIS Installation

After installation, the server configuration was reviewed to confirm that the IIS role had been successfully added.
<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/7a3258c2-a07a-47fe-bf0f-71ebe007d623" />



### Validation Principle

A configuration change should not be considered complete simply because a command or installation process finishes.

The resulting system state should be verified.

This project follows that approach by documenting the configuration and then validating the result.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/9ec12a44-d80c-4b8a-b29f-65d1df0985d7" />


---

# 🔟 Remove IIS

The IIS Web Server role was subsequently removed.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/ccf76f59-3a50-4f00-957a-f55cb7717470" />


<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/d2a51323-ec64-401f-aac9-2d875eea031e" />



The final verification confirmed that IIS was no longer installed.

<img width="1247" height="806" alt="image" src="https://github.com/user-attachments/assets/80a835e1-c0da-4477-8f48-898679407a1f" />


### 🔐 Security Relevance

Removing unnecessary services and server roles follows the security principle of **least functionality**.

If a service is not required, disabling or removing it can reduce:

* Exposed services
* Potential attack surface
* Unnecessary software components
* Administrative complexity

---

# ✅ Validation Results

| Test / Configuration                 | Result      |
| ------------------------------------ | ----------- |
| Existing IP information collected    | ✅ Verified  |
| Network configuration reviewed       | ✅ Verified  |
| Static IPv4 configuration            | ✅ Completed |
| Server renamed                       | ✅ Completed |
| Windows Update configuration changed | ✅ Completed |
| Server restarted                     | ✅ Completed |
| IIS installed                        | ✅ Verified  |
| IIS role validated                   | ✅ Verified  |
| IIS removed                          | ✅ Verified  |
| Final configuration documented       | ✅ Completed |

---

# 🛡️ Cybersecurity Relevance

Although this project focused primarily on Windows Server administration, the tasks demonstrate several foundational cybersecurity concepts.

## Attack Surface Reduction

Installing and removing IIS demonstrated how unnecessary server functionality can be removed to reduce the attack surface.

## Patch Management

Windows Update configuration demonstrated the importance of maintaining a controlled patch-management process.

## Configuration Management

Network and system configuration changes were documented and validated instead of being performed without verification.

## Least Functionality

The IIS installation and removal lifecycle demonstrated that servers should only run the services and roles required for their intended purpose.

## Infrastructure Security

Understanding how servers are configured provides the foundation for more advanced security activities such as:

* Vulnerability assessment
* Security monitoring
* Firewall configuration
* System hardening
* Incident response
* Log analysis

---

# 📊 Technical Skills Demonstrated

### Windows Server

* Windows Server 2019 administration
* Server role management
* IIS administration
* Network configuration
* IPv4 addressing
* Windows Update management
* System restart and validation

### PowerShell

Get-NetIPAddress
Get-NetIPConfiguration
New-NetIPAddress
Rename-Computer
Restart-Computer

### Security Concepts

* Attack surface reduction
* Least functionality
* Patch management
* Configuration validation
* Secure infrastructure
* System administration

---

# 🧠 Lessons Learned

This project reinforced the importance of understanding the relationship between **system administration and cybersecurity**.

PowerShell provides an efficient and repeatable method for managing Windows Server systems. The same command-line skills used to configure a server can also be expanded into automation, security auditing, system hardening, and incident-response workflows.

The project also demonstrated that configuration changes should be **intentional, documented, and validated**.

A secure server is not simply a server with security software installed. Security begins with understanding what the system is running, how it is configured, what services are exposed, and whether those services are actually required.

---

# 🚀 Future Security Enhancements

The next stage of this project would be to transform the Windows Server environment into a more complete security lab.

### Planned Improvements

* [ ] Configure and harden Windows Firewall
* [ ] Implement local security policies
* [ ] Configure user and group permissions
* [ ] Deploy Active Directory
* [ ] Develop PowerShell security-auditing scripts
* [ ] Install and configure Sysmon
* [ ] Monitor Windows Event Logs
* [ ] Perform a Nessus vulnerability assessment
* [ ] Perform Nmap network validation
* [ ] Forward Windows security logs to Splunk
* [ ] Develop automated PowerShell hardening scripts
* [ ] Perform before-and-after security validation

---

# 📁 Repository Structure
Windows-Server-2019-Configuration-via-Powershell-CLI/
│
├── README.md
│
└── assets/
    ├── 01-get-netipaddress.jpg
    ├── 02-get-netipconfiguration.jpg
    ├── 03-static-ip-configuration.jpg
    ├── 04-rename-computer.jpg
    ├── 05-sconfig-update-settings.jpg
    ├── 06-manual-update-confirmation.jpg
    ├── 07-restart-computer.jpg
    ├── 08-iis-role-installation.jpg
    ├── 09-iis-role-verification.jpg
    └── 10-iis-role-removed.jpg

---

# 📸 Project Evidence
The evidence follows the project lifecycle:

Baseline
   ↓
Configuration
   ↓
Validation
   ↓
Service Deployment
   ↓
Service Validation
   ↓
Service Removal
   ↓
Final State

# 🎓 Project Takeaway

This project provided practical experience with **Windows Server 2019, PowerShell, network configuration, Windows Update management, IIS, and server administration**.

More importantly, it established a foundation for security-focused infrastructure work. Understanding how to configure and manage Windows systems is essential for roles involving **SOC operations, vulnerability management, system security, and security engineering**.

The project can be further expanded into a full Windows security lab by adding vulnerability scanning, centralized logging, endpoint monitoring, firewall hardening, Active Directory, and PowerShell-based security automation.

---

## 👤 Author

### Sean Redding

**Cybersecurity | Security Operations | Vulnerability Management | Security Engineering**

* 🌐 **GitHub:** [https://github.com/SealT6](https://github.com/SealT6)
* 💼 **LinkedIn:** [https://www.linkedin.com/in/sean-redding-aa503a293/](https://www.linkedin.com/in/sean-redding-aa503a293/)
