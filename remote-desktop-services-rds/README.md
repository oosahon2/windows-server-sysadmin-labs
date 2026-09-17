# Remote Desktop Services (RDS) Lab

## Overview

In this lab, I installed and configured Remote Desktop Services (RDS) on Windows Server and tested both RemoteApp and full Remote Desktop access.

The goal was to understand how users can remotely access applications or a complete desktop session hosted on another Windows Server.

## Lab Environment

- Domain: bobby.local
- RDS Server: SERVER3
- Client/Test Server: SERVER2
- SERVER3 IP Address: 192.168.163.120
- Domain User Used for Testing: BOBBY\david.wilson
- Virtualization Platform: VMware Workstation

## RDS Deployment

On SERVER3, I installed Remote Desktop Services using:

- Remote Desktop Services Installation
- Quick Start
- Session-based desktop deployment

The following RDS role services were installed:

- RD Connection Broker
- RD Web Access
- RD Session Host

The deployment completed successfully and created a Quick Session Collection.

## Session Collection

The Quick Session Collection was configured with:

- Host Server: SERVER3
- User Group: BOBBY\Domain Users
- RemoteApps:
  - Calculator
  - Paint

This allowed normal domain users to access published RDS resources.

## RD Web Access

RD Web Access was tested from SERVER2 using:

https://SERVER3.bobby.local/rdweb

Initially, the connection failed with:

ERR_SSL_KEY_USAGE_INCOMPATIBLE

I checked the RDS deployment certificate configuration and discovered that the RDS certificates were not configured.

A new certificate was created for:

SERVER3.bobby.local

The certificate was assigned to RD Web Access.

After the certificate was configured, the original SSL error was resolved.

Because the lab certificate was self-signed, SERVER2 displayed:

NET::ERR_CERT_AUTHORITY_INVALID

For the lab environment, I continued using the known self-signed certificate.

## RemoteApp Test

I logged into RD Web Access from SERVER2 using:

BOBBY\david.wilson

The user successfully authenticated and could see the published applications:

- Calculator
- Paint

I launched Calculator from RD Web Access.

An RDP file was downloaded and opened.

After authenticating again as David Wilson, Calculator successfully launched as a RemoteApp from SERVER3.

This proved that the application was running through Remote Desktop Services while appearing on SERVER2.

## Full Remote Desktop Test

I also tested a full Remote Desktop session.

From SERVER2, I opened Remote Desktop Connection using:

mstsc

I connected to:

SERVER3.bobby.local

I authenticated using a normal domain user account.

The connection opened a full Windows desktop session on SERVER3.

This demonstrated the difference between RemoteApp and Remote Desktop.

## RemoteApp vs Remote Desktop

RemoteApp:

SERVER2 → SERVER3 → Published Application Only

Example:

SERVER2 → SERVER3 → Calculator

Remote Desktop:

SERVER2 → SERVER3 → Full Windows Desktop Session

RemoteApp gives the user access only to applications published by the administrator.

Remote Desktop gives the user a full desktop session on the remote server, but the user's permissions still control what they are allowed to access.

## RDS Components Learned

### RD Session Host

Hosts user sessions and runs the applications or desktop environment.

### RD Connection Broker

Manages RDS connections and helps reconnect users to existing sessions.

### RD Web Access

Provides a web portal where users can access published RemoteApps and desktops.

### Session Collection

Groups RDS resources and controls which users or groups can access them.

### RemoteApp

Allows individual applications to be delivered remotely without giving the user the full server desktop.

## Troubleshooting Performed

During this lab, I worked through several issues:

- PowerShell Remoting initially blocked the RDS deployment
- Verified WinRM using Test-WSMan
- Successfully used Enter-PSSession between SERVER2 and SERVER3
- Resolved an SSL certificate usage error
- Configured an RDS certificate
- Identified the difference between an invalid certificate configuration and an untrusted self-signed certificate
- Verified domain user permissions
- Tested both RemoteApp and full Remote Desktop access

## Commands Used

```powershell
Test-WSMan SERVER3.bobby.local

Enter-PSSession -ComputerName SERVER3.bobby.local

hostname

mstsc
