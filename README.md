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
