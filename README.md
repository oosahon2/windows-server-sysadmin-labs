# Windows Server System Administration Home Lab

This repository documents my hands-on Windows Server system administration labs as I build practical skills in managing Windows Server environments.

My lab environment is built using VMware Workstation and Windows Server. The goal of this portfolio is to demonstrate practical experience configuring, administering, and troubleshooting common Windows Server services.

## Lab Environment

- VMware Workstation
- Windows Server
- Active Directory Domain Services (AD DS)
- Domain: bobby.local
- Windows Server virtual machines
- PowerShell and Windows administrative tools

## Skills & Labs

### Active Directory
- Installed Active Directory Domain Services
- Promoted a Windows Server to a Domain Controller
- Created and managed users, groups, and Organizational Units (OUs)
- Joined additional servers to the domain

### DNS
- Configured DNS for the Active Directory environment
- Created A, CNAME, and PTR records
- Tested name resolution using `nslookup`

### DHCP
- Installed and configured the DHCP Server role
- Created and activated a DHCP scope
- Configured scope options including default gateway and DNS
- Configured DHCP exclusions and lease duration
- Created a DHCP reservation using a client's MAC address
- Tested DHCP configuration using `ipconfig /release`, `ipconfig /renew`, and `ipconfig /all`

### Group Policy
- Created and linked Group Policy Objects (GPOs)
- Applied policies to Organizational Units
- Tested and troubleshot Group Policy application
- Used `gpupdate /force` and `gpresult` for verification

### FSMO Roles
- Learned the purpose of the five FSMO roles
- Identified FSMO role holders using `netdom query fsmo`

## Troubleshooting Experience

Throughout these labs, I practiced troubleshooting:

- DNS and name-resolution problems
- DHCP configuration problems
- Domain connectivity
- Group Policy application
- Active Directory communication
- VMware virtual networking

## Upcoming Labs

- IIS Web Server
- PowerShell administration
- Additional Windows Server administration and troubleshooting labs

## Purpose

I am building this portfolio to demonstrate practical Windows Server administration skills and document my progression toward System Administrator and IT Systems roles.
