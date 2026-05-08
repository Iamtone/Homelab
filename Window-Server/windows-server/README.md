# Anthony's Homelab

## Environment
- Hypervisor: VMware Workstation Pro
- Host Machine: Windows 11, 1TB SSD

## Lab 1 — Windows Server 2025 Domain Controller
- Installed Windows Server 2025 Datacenter Evaluation
- Promoted to Domain Controller
- Domain: Nwekeze.Local
- Configured DNS and DHCP
- Joined CLIENT01 to domain

## What I Learned
- DNS must point to the DC or domain join fails
- Static IPs are required for infrastructure roles
- VM files must be stored outside OneDrive sync paths

## Errors I Hit and Fixed
- .lck file lock error — caused by storing VMs in OneDrive path
- IPv6 DNS conflicts — resolved by managing IPv6 entries explicitly