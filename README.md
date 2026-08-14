# 🖥️ Windows Server 2019 Configuration with PowerShell

## 📌 Project Overview

This project demonstrates hands-on **Windows Server administration and PowerShell-based system configuration** in a virtualized lab environment.

The project focused on preparing a Windows Server system, inspecting and configuring network settings, renaming the computer, managing Windows Update behavior, restarting the server, and installing and removing the **Web Server (IIS)** role.

The goal of this project was to develop practical experience with repeatable command-line administration while validating configuration changes through PowerShell output and Windows Server management tools.

> **Portfolio Focus:** This project demonstrates the relationship between system administration, network configuration, automation, service management, and security-minded server administration.

---

## 🎯 Project Objectives

- Inspect existing Windows network configuration using PowerShell
- Configure a static IPv4 address
- Configure the subnet prefix and default gateway
- Rename the Windows Server computer
- Modify Windows Update behavior
- Restart the server to apply configuration changes
- Install the IIS Web Server role
- Verify that IIS was successfully installed
- Remove the IIS Web Server role
- Validate and document configuration changes

---

## 🏗️ Lab Environment

| Component | Configuration |
|---|---|
| Operating System | Windows Server 2019 |
| Administration | Microsoft PowerShell |
| Environment | Virtualized Lab |
| Web Server | IIS |
| Primary Focus | Windows Server Configuration |
| Networking | IPv4 / TCP-IP |

---

## 🧰 Tools & Technologies

- **Windows Server 2019**
- **Microsoft PowerShell**
- **Server Manager**
- **IIS (Internet Information Services)**
- **Windows `sconfig` Utility**
- **Windows Networking Cmdlets**
- **Virtualization**

---

# 🔧 Configuration Process

## 1. Inspect Existing Network Configuration

The first step was to collect information about the server's existing network configuration before making changes.

The following PowerShell command was used:

```powershell
Get-NetIPAddress
This command was used to identify existing IP addresses, interface indexes, address families, and prefix lengths.
2. Review the Current IP Configuration
The existing network configuration was reviewed using:
Get-NetIPConfiguration
This provided information about the current IP configuration, network interface, and default gateway.
3. Configure a Static IPv4 Address
A static IPv4 configuration was assigned to the server using PowerShell.
New-NetIPAddress -IPAddress 192.168.50.5 -InterfaceIndex 13 -PrefixLength 24 -DefaultGateway 192.168.50.2
This command demonstrates how PowerShell can be used to configure:
IPv4 address
Network interface
Prefix length
Default gateway
Note: The IP address and gateway shown above were used within the lab environment and should not be considered production network configuration.
4. Rename the Windows Server
The server computer name was changed using PowerShell rather than relying exclusively on the graphical interface.
Rename-Computer -NewName "NewPCName" -Force -PassThru
The -PassThru parameter was used to return the resulting computer-name information for verification.
5. Configure Windows Update
The Windows Server sconfig utility was used to modify the Windows Update configuration.
sconfig
The update configuration was changed from automatic updates to manual updates within the lab environment.
6. Verify Windows Update Configuration
The resulting configuration was reviewed to verify that the update setting had been changed successfully.
🔐 Security Consideration
Manual update configuration can provide administrators with greater control over when updates are applied. However, delaying security updates can increase a system's exposure to known vulnerabilities.
In a production environment, this type of configuration should be supported by:
Centralized patch management
Defined maintenance windows
Patch compliance monitoring
Vulnerability scanning
Change management procedures
7. Restart the Server
The server was restarted after configuration changes were made.
Restart-Computer
Restarting the system provided an opportunity to apply configuration changes and verify that the server could successfully return to an operational state.
🌐 IIS Web Server Configuration
8. Install the IIS Web Server Role
The Internet Information Services (IIS) Web Server role was installed using Windows Server's Server Manager.
The installation process followed:
Server Manager
      ↓
Manage
      ↓
Add Roles and Features
      ↓
Web Server (IIS)
Although this project primarily focused on PowerShell-based administration, the IIS installation demonstrates practical Windows Server role management.
9. Verify IIS Installation
After the IIS role was installed, the server configuration was reviewed to verify that the Web Server role was successfully added.
This validation step demonstrates the importance of confirming that configuration changes produce the expected result.
10. Remove the IIS Role
The IIS Web Server role was subsequently removed from the server.
The final verification confirmed that the IIS role was no longer installed.
This completed the installation, validation, and removal lifecycle for the server role.
✅ Validation Results
Configuration / Test	Result
Existing IP information collected	✅ Verified
Existing IP configuration reviewed	✅ Verified
Static IPv4 configuration	✅ Completed
Computer rename	✅ Completed
Windows Update configuration	✅ Completed
Server restart	✅ Completed
IIS installation	✅ Verified
IIS removal	✅ Verified
Final configuration documented	✅ Completed
🛡️ Security Considerations
Although this project primarily focused on Windows Server administration, several of the tasks directly relate to cybersecurity and secure infrastructure management.
Network Configuration
Properly configuring network interfaces and IP addressing is an important component of secure infrastructure management. Understanding the server's network configuration helps administrators identify how the system communicates with other hosts and services.
Patch Management
The project demonstrated changing Windows Update behavior. In a production environment, patching should be centrally managed and monitored to reduce the risk associated with missing security updates.
Attack Surface Reduction
The IIS installation and removal process demonstrates the principle of least functionality.
If a server does not require a particular service or role, removing it can reduce the number of exposed services and potentially decrease the system's attack surface.
Configuration Validation
Configuration changes were followed by verification steps rather than assuming that the changes were successful.
This is an important security and administration practice because configuration errors can create unexpected security risks.
PowerShell Administration
PowerShell provides administrators with a repeatable method for managing Windows systems.
The commands used in this project could be expanded into automated configuration and security-hardening scripts.
📊 Skills Demonstrated
Windows Server Administration
Windows Server 2019 configuration
Network configuration
IPv4 addressing
Computer naming
Windows Update management
IIS role management
System restart and validation
PowerShell
Get-NetIPAddress
Get-NetIPConfiguration
New-NetIPAddress
Rename-Computer
Restart-Computer
Command-line system administration
Cybersecurity Foundations
Attack surface reduction
Patch management
Least functionality
Configuration validation
Secure infrastructure concepts
System administration
🧠 Lessons Learned
This project reinforced the importance of understanding how Windows Server systems are configured and managed from the command line.
PowerShell provides administrators with an efficient and repeatable way to gather system information and modify server settings. Using PowerShell for network configuration and system administration also provides a foundation for developing automated administrative and security scripts.
The project also demonstrated that system administration and cybersecurity are closely connected. Network configuration, patch management, service installation, and removal of unnecessary server roles can all affect a system's overall security posture.
A major takeaway from this project was the importance of making configuration changes intentionally and then validating that the changes were successfully applied.
🚀 Future Improvements
I plan to expand this project into a more security-focused Windows Server lab by implementing additional security controls and monitoring capabilities.
Potential improvements include:
 Configure Windows Firewall rules
 Implement local security policies
 Configure user and group permissions
 Deploy Active Directory
 Create PowerShell security-auditing scripts
 Install and configure Sysmon
 Monitor Windows Event Logs
 Perform a Nessus vulnerability assessment
 Perform Nmap network validation
 Forward security logs to Splunk
 Develop automated PowerShell hardening scripts
 Perform before-and-after security validation
📁 Project Structure
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
🔄 Configuration Workflow
Network Discovery
       │
       ▼
IP Configuration Review
       │
       ▼
Static IP Assignment
       │
       ▼
Computer Renaming
       │
       ▼
Windows Update Configuration
       │
       ▼
Server Restart
       │
       ▼
IIS Installation
       │
       ▼
IIS Verification
       │
       ▼
IIS Removal
       │
       ▼
Final Validation
📚 Project Takeaway
This project provided hands-on experience with Windows Server configuration, PowerShell administration, network configuration, Windows Update management, and IIS role management.
More importantly, it demonstrated how traditional system administration tasks can contribute to an organization's overall cybersecurity posture.
The project serves as a foundation for future work involving Windows security, vulnerability management, security monitoring, PowerShell automation, and security engineering.
👤 Author
Sean Redding
Cybersecurity | Security Operations | Vulnerability Management | Security Engineering
GitHub: https://github.com/SealT6
LinkedIn: https://www.linkedin.com/in/sean-redding-aa503a293/

