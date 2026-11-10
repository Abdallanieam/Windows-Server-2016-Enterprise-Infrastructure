<img width="1920" height="1022" alt="22" src="https://github.com/user-attachments/assets/d4e53986-b395-4152-bdbf-e2e704219866" />

**Microsoft MCSA | Enterprise Network Infrastructure & Administration**

---

## 📌 Project Overview

This project demonstrates the deployment, configuration, and administration of an enterprise IT infrastructure using **Microsoft Windows Server 2016** in a virtualized environment powered by VMware Workstation.

The lab covers essential enterprise infrastructure services, centralized administration, network high availability, endpoint security, storage management, virtualization, and disaster recovery.

The implementation includes Active Directory Domain Services, DNS, DHCP Failover, Group Policy Management, IIS Web Hosting, File Server Resource Manager, Hyper-V Virtualization, Hyper-V Replica, and Windows Server Backup.

## 🏗️ Lab Environment & Network Topology

The environment consists of multiple Windows Server and Windows Client machines connected through a virtual network.

| Hostname | Operating System | Primary Role | IP Address |
|---|---|---|---|
| PDC / TEST | Windows Server 2016 GUI | Primary Domain Controller, AD DS, DNS, DHCP, IIS | 192.168.1.2/24 |
| CORE | Windows Server 2016 Core | Server Core & Hyper-V Replica Host | 192.168.1.3/24 |
| win-domain | Windows 10 Enterprise | Domain Member Client | 192.168.1.40 (DHCP) |
| FATHY / AHMED | Windows 10 | Domain User Test Accounts | DHCP |

**Domain Name:** `xyz.local`

**Network Configuration:**
- Network: `192.168.1.0/24`
- Default Gateway: `192.168.1.1`
- DNS Server: `192.168.1.2`
- DHCP Server: `192.168.1.2`

## 🎯 Lab Objectives

- Deploy and configure Active Directory Domain Services.
- Configure centralized DNS and DHCP services.
- Implement DHCP Failover using Hot Standby mode.
- Manage domain users, computers, and Group Policies.
- Apply enterprise endpoint security restrictions.
- Deploy an internal website using IIS.
- Configure centralized printer management.
- Implement shared folders and NTFS permissions.
- Configure File Server Resource Manager (FSRM).
- Deploy nested virtualization using Hyper-V.
- Implement Hyper-V Replica for high availability.
- Configure Windows Server Backup and disaster recovery.

## 🛠️ Implementation & Lab Modules

### Module A: Core Infrastructure & Domain Deployment

**Page 01 – VMware Workstation & Server Infrastructure**
- Designed the virtual network topology using VMware Workstation.
- Deployed Windows Server 2016.
- Installed the following roles:
  - Active Directory Domain Services (AD DS).
  - DNS Server.
  - DHCP Server.
  - File and Storage Services.
  - IIS.
  - Print Services.
  - Windows Deployment Services (WDS).
- Configured the PDC network interface with `192.168.1.2/24`.

**Page 02 – Windows Server Core Configuration**
- Deployed Windows Server 2016 Server Core.
- Configured the hostname as `CORE`.
- Assigned a static IP address.
- Enabled remote management.
- Enabled PowerShell Remoting.
- Configured Windows Updates using `sconfig`.

**Page 03 – DHCP Client Verification**
- Verified client network configuration.
- Inspected active DHCP leases.
- Confirmed the following network settings:
  - Subnet: `192.168.1.0/24`
  - Gateway: `192.168.1.1`
  - DNS: `192.168.1.2`
  - Client IP: `192.168.1.40`

**Page 04 – Centralized Server Management**
- Added remote servers (CORE and TEST) to Server Manager.
- Configured domain deployment credentials.
- Used domain administrator authentication.
- Managed multiple servers through a centralized console.

### Module B: Group Policy Management & Security Hardening

**Page 05 – Centralized Desktop Wallpaper**
- Configured User Configuration GPO.
- Enabled Desktop Wallpaper policy.
- Configured the shared wallpaper path:

`\\TEST\pix\1.jpg`

- Set wallpaper style to Stretch.
- Prevented users from changing desktop backgrounds.

**Page 06 – Password Policy & User Interface Restrictions**
- Configured domain password policies:
  - Password History: 3 passwords.
  - Maximum Password Age: 42 days.
  - Minimum Password Age: 1 day.
  - Minimum Password Length: 7 characters.
  - Password Complexity: Enabled.
- Restricted users from changing:
  - Desktop Background.
  - Color and Appearance.

**Page 07 – Removable Storage Restrictions**
- Configured removable storage restrictions through GPO.
- Enabled Deny All Access for removable storage classes.
- Enabled Deny Write Access for CD/DVD devices.

**Page 08 – Windows Firewall & Remote Assistance**
- Configured Windows Defender Firewall settings through GPO.
- Managed inbound and outbound Remote Assistance rules.
- Configured TCP/UDP access rules.
- Managed related service startup settings and firewall logging.

### Module C: DNS & IIS Web Hosting

**Page 09 – Enterprise Intranet Web Server**
- Installed Internet Information Services (IIS).
- Hosted an internal enterprise website.
- Configured a DNS Host (A) Record:

| Record | Value |
|---|---|
| Hostname | www |
| Domain | xyz.local |
| IP Address | 192.168.1.2 |

- Configured IIS website binding on HTTP port `80`.
- Used the default website directory:

`C:\inetpub\wwwroot`

- Verified website access through the internal DNS name:

`http://www.xyz.local`

### Module D: DHCP High Availability & Domain Management

**Page 10 – DHCP Failover Configuration**
- Configured DHCP Failover between server nodes.
- Selected Hot Standby mode.
- Configured State Switchover Interval as Disabled.
- Reserved 5% of the IP address pool for standby server failover.

**Page 11 – Windows Client Domain Join**
- Joined Windows 10 client to `xyz.local`.
- Authenticated using Domain Administrator credentials.
- Verified computer registration through Active Directory Users and Computers (ADUC).
- Tested network connectivity using ICMP ping.

### Module E: Print Management & Hyper-V Installation

**Page 12 – Enterprise Print Server**
- Installed Print and Document Services.
- Managed centralized network printer queues.
- Configured Microsoft Print to PDF and XPS Document Writer.
- Managed printer drivers and sharing settings.

**Page 13 – GPO Printer Deployment & Hyper-V**
- Configured printer deployment using Group Policy Preferences.
- Implemented per-user and per-machine printer deployment.
- Installed the Hyper-V role.
- Installed Hyper-V Management Tools.
- Installed Hyper-V PowerShell Module.

### Module F: File Sharing & NTFS Access Control

**Page 14 – Shared Folders & Network Drive Mapping**
- Created shared storage directory:

`E:\public`

- Configured shared folder permissions.
- Created a GPO Drive Map for network drive `H:`.
- Mapped the following UNC path:

`\\TEST\public`

- Configured NTFS permissions:
  - SYSTEM: Full Control.
  - Administrators: Full Control.
  - HR-GROUP: Read & Execute.
  - IT-GROUP: Read & Execute.

**Page 15 – NTFS Permission Verification**
- Tested access restrictions using domain accounts FATHY and AHMED.
- Verified access control for HR, IT, and Sales directories.
- Confirmed unauthorized users received access-denied messages.

**Page 16 – Active Directory Recycle Bin**
- Enabled Active Directory Recycle Bin through Active Directory Administrative Center (ADAC).
- Activated the feature for domain `xyz.local`.
- Verified the activation process.

**Page 17 – Network Drive Verification**
- Verified mapped network drives on domain clients.
- Tested access to shared folders.
- Confirmed network drive availability through Windows File Explorer.

### Module G: File Server Resource Manager (FSRM)

**Page 18 – File Screening Configuration**
- Installed and configured File Server Resource Manager.
- Created file screening rules on:

`E:\public`

- Applied the Block Audio and Video Files template.
- Configured restrictions for:
  - Executable Files.
  - Image Files.
  - Audio and Video Files.
  - Text Files.
  - Web Files.

**Page 19 – Server Infrastructure Health Check**
- Reviewed infrastructure status through Server Manager.
- Verified installed server roles:
  - AD DS.
  - DNS.
  - DHCP.
  - File Services.
  - Hyper-V.
  - IIS.
  - Print Services.
  - WDS.

### Module H: Nested Virtualization & Hyper-V Replica

**Page 20 – Hyper-V Virtual Machine Deployment**
- Created a Generation 2 virtual machine named `VM1`.
- Configured virtual machine resources:

| Component | Configuration |
|---|---|
| VM Name | VM1 |
| Generation | Generation 2 |
| Startup RAM | 2048 MB |
| Virtual Switch | vsw1 |
| Virtual Disk | Dynamic VHDX |
| Disk Name | VM1.vhdx |
| Operating System | Windows Server 2016 |

**Page 21 – Nested Virtualization & Replica Configuration**
- Installed Windows Server 2016 inside VM1.
- Initialized the Hyper-V Enable Replication wizard.
- Selected CORE as the Replica Host.
- Configured Kerberos authentication.
- Used HTTP over TCP port `80`.

**Page 22 – Hyper-V Replica Authorization**
- Enabled Hyper-V Replica Server settings on TEST and CORE.
- Configured Kerberos Authentication.
- Enabled HTTP replication on port `80`.
- Authorized replication from specified servers.
- Configured the default virtual hard disk storage directory.

### Module I: Disaster Recovery & Windows Server Backup

**Page 23 – Windows Server Backup Configuration**
- Configured backup settings using Windows Server Backup.
- Selected critical infrastructure components:
  - System State.
  - Bare Metal Recovery.
  - Host Components.
  - Virtual Machine Guest Disks (VM1OffLine).

**Page 24 – Backup Execution & Verification**
- Executed Backup Once operation.
- Selected New Volume `G:` as the backup destination.
- Used VSS Copy Backup.
- Reviewed backup execution logs.
- Verified successful backup completion:

`Completed with status: Backup succeeded`

## 💻 Technology Stack

| Category | Technologies |
|---|---|
| Operating Systems | Windows Server 2016, Windows 10 Enterprise |
| Directory Services | Active Directory DS, ADAC, AD Recycle Bin |
| Network Services | DNS, DHCP, DHCP Failover |
| Web Services | IIS 10.0, HTTP, DNS Records |
| Security & Policies | GPO, Windows Firewall, Password Policies, USB Restrictions |
| File Services | SMB Shares, NTFS ACLs, FSRM, File Screening |
| Virtualization | VMware Workstation, Hyper-V, Nested Virtualization |
| High Availability | DHCP Failover, Hyper-V Replica, Kerberos |
| Backup & Recovery | Windows Server Backup, VSS, System State, Bare Metal Recovery |
| Administration | Server Manager, PowerShell, Server Core, sconfig |

## 📚 Skills Developed

- Windows Server Deployment and Administration.
- Active Directory Domain Services Management.
- DNS and DHCP Infrastructure Configuration.
- DHCP High Availability and Failover.
- Group Policy Management and Endpoint Hardening.
- Windows Firewall and Remote Assistance Management.
- IIS Web Hosting and DNS Integration.
- Enterprise File Sharing and NTFS Permissions.
- File Server Resource Manager and File Screening.
- Centralized Print Management.
- Hyper-V Virtualization and Replica Configuration.
- Windows Server Backup and Disaster Recovery.
- Remote Server Administration using Server Manager and PowerShell.

## 👨‍💻 Author

**Abdalla Mohamed Nieam**

Network & Systems Infrastructure Engineer

Focused on Microsoft Enterprise Infrastructure, Windows Server Administration, Active Directory, Network Services, Virtualization, and Infrastructure High Availability.

**GitHub:** [Abdallanieam](https://github.com/Abdallanieam)

---

*This project was implemented as a practical MCSA Enterprise Infrastructure and Administration lab using VMware Workstation.*<img width="1920" height="1022" alt="22" src="https://github.com/user-attachments/assets/dad58ecd-950b-49b1-962a-9d8108c18f02" />
<img width="1920" height="1022" alt="22" src="https://github.com/user-attachments/assets/5c5c5cca-587e-4584-90a5-fa1a1f8a9154" />
