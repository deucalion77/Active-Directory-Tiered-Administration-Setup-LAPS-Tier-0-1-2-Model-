# 🧱 Active Directory Tiered Administration Setup (LAPS + Tier 0/1/2 Model)

This repository documents the PowerShell commands and Group Policy configuration steps used to implement a **three-tier Active Directory (AD) administration model** with **LAPS** (Local Administrator Password Solution).

It was built and tested in a lab environment as part of the research project *“Attack and Defense Mechanisms in Active Directory Environments.”*

---

## 🎯 Overview

This configuration implements Microsoft’s **Tiered Administration Model** to prevent credential leakage and lateral movement by separating admin accounts, devices, and permissions into isolated security tiers.

| Tier | Purpose | Example Systems | Who Can Log On |
|------|----------|-----------------|----------------|
| **Tier 0** | Domain infrastructure | Domain Controllers, Admin Workstations | Domain Admins only |
| **Tier 1** | Servers / services | MySQL Server, File Servers, App Servers | ServerAdmins |
| **Tier 2** | End-user endpoints | User Workstations, Laptops | Regular Users, LAPS Local Admins |

**Key defensive controls**
- Local Administrator Password Solution (LAPS)
- Deny logon policies for higher tiers on lower-tier devices
- Group Managed Service Accounts (gMSA) for server services
- Protected Users group & LSASS protection

---

## 🧭 Organizational Unit (OU) Structure

Under the root OU **Organization**, create three main sub-OUs:
