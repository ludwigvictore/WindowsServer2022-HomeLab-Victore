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
