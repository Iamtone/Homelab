# Anthony's Homelab

## Environment
- Hypervisor: VMware Workstation Pro
- Host Machine: Windows 11, 1TB SSD

## Lab 1 — Windows Server 2025 Domain Controller
- Installed Windows Server 2025 Datacenter Evaluation
- Promoted to Domain Controller
- Domain: Nwekeze.Local
- Configured DNS and DHCP
- Joined CLIENT01 Virtual Machine to domain

## What I Learned
- DNS must point to the DC or domain join fails
- Static IPs are required for infrastructure roles
- VM files must be stored outside OneDrive sync paths

## Errors I Hit and Fixed
- .lck file lock error — caused by storing VMs in OneDrive path
- IPv6 DNS conflicts — resolved by managing IPv6 entries explicitly



## Active Directory Structure (5/9/26)

## Domain
- Domain Name: Nwekeze.Local
- Domain Controller: Windows Server 2025

## Organizational Units
- IT Department
- HR Department
- Student


## Users Created
- Created 6 users in total and placing 2 in each IT Department, HR Department and Student OU.

## Client Machine
- CLIENT01 joined to Nwekeze.Local domain.
- Logged into CLIENT01 using my domain account for the first time. 
- Didn't expect it to work on the first try but it did. CLIENT01 had no idea who I was locally — it had to ask the DC. That's when it clicked for me how AD actually works.


## Additional Lessons Learned
- Computer must be renamed to CLIENT01 before domain join for clean AD records.
- Joining the Domain requires the Domain Controller to check and authorize your account.
- Authentication flows from CLIENT01 -> DC -> approval, the workstation never decides on its own.


## Group Policy Objects (5/12/26)

### What is Group Policy
Group Policy lets you push settings and rules from the Domain Controller to every machine and user in the domain automatically. No touching each machine individually.

### GPO 1 — IT Department Policy
- Linked to: IT Department OU
- Setting: Screen lock timeout after 5 minutes of inactivity
- Why: Forces machines to lock automatically for security

### GPO 2 — Wallpaper Policy
- Linked to: Students OU
- Setting: Forces a specific desktop wallpaper for all student accounts
- Why: Practiced applying different policies to different OUs

### How I verified it worked
- Ran gpupdate /force on CLIENT01
- Ran gpresult /r to confirm policies applied
- Logged in as a student account and confirmed wallpaper changed