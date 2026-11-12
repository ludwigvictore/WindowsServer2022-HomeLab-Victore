# WindowsServer2022-HomeLab-Victore

This repository contains the complete documentation, configuration details, and scripts for my Windows Server 2022 home lab setup.

---

## Hardware Specs (ITX Desktop Setup)
* **Processor:** Intel i5-13400 (2500MHz, 10 Cores, 16 Threads)
* **Motherboard:** ASRock B660M-ITX/ac
* **RAM:** 16GB (2x 8GB G.Skill TridentZ RGB)
* **Storage:** 500GB Samsung SSD
* **GPU:** ASUS Radeon RX-7600
* **Case:** PCCooler i100

---

## Network Topology & IP Schema

| Hostname | Role / Description | OS | IP Address | Subnet Mask | Preferred DNS |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Server-local | Domain Controller / Primary DNS | Windows Server 2022 | 192.168.1.178 *(Static)* | 255.255.255.0 | 127.0.0.1 |

---

## Active Directory Architecture
* **Domain FQDN:** `homelab.local`
* **NetBIOS Name:** `Server-Victore`
* **Primary Domain Controller:** `Server-local.homelab.local`
* **Forest / Domain Functional Level:** Windows Server 2022

### Proposed Organizational Unit (OU) Structure

```text
homelab.local
 └── HOMELAB-Objects
      ├── OU=Servers
      ├── OU=Workstations
      ├── OU=Users
      └── OU=Groups
      └── OU=VM


###Hypervisor/Hyper-V
Added server roles for Hyper-V Manager
Configured two VDI with following specs:

VM Name: VictoreGen2VM001
OS: Windows11 Home
Processor: 2 Virtual Processor
Memory: 4096mb
OS Installation: Used ISO for the OS installation
This VDI cannot be joined to the Domain Controller because Windows11 has been installed

OS: Windows11 Pro (Massgrave activation)
VM Name: VictoreGen2VM002
Processor: 2 Virtual Processor
Memory: 4096mb
OS Installation: Used ISO for the OS installation
This VDI cannot be joined to the domain Controller yet because the physical ethernet adapter settings is conflicting with vEthernet adapter IP

###Group Policy Management
Added GPO for Account Lockout policy
Added GPO to remove delay Login after failed attempts

###Enabled RPC from services.msc on server to enable joining Virtual Machine via Powershell
