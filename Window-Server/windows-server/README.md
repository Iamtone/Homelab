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

## Users Created
- Anthony.Nwekeze (IT Department OU)

## Client Machine
- CLIENT01 joined to Nwekeze.Local domain.
- Logged into CLIENT01 using my domain account for the first time. 
- Didn't expect it to work on the first try but it did. CLIENT01 had no idea who I was locally — it had to ask the DC. That's when it clicked for me how AD actually works.


## Additional Lessons Learned
- Computer must be renamed to CLIENT01 before domain join for clean AD records.
- Joining the Domain requires the Domain Controller to check and authorize your account.
- Authentication flows from CLIENT01 -> DC -> approval, the workstation never decides on its own.