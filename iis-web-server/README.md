# IIS Web Server Deployment Lab

## Overview

In this lab, I installed and configured the Web Server (IIS) role on Windows Server and deployed a custom HTML webpage.

I then tested the website locally on the IIS server and remotely from another Windows Server machine to verify network connectivity and successful HTTP communication.

## Lab Environment

- Windows Server
- VMware Workstation
- Active Directory domain: bobby.local
- IIS Web Server
- Web Server: SERVER2
- Client/Test Machine: SERVER3
- Web Server IP: 192.168.163.10

## What I Accomplished

- Installed the Web Server (IIS) role
- Configured IIS on SERVER2
- Created a custom `index.html` webpage
- Hosted the webpage from the IIS web root
- Verified the website locally using `http://localhost`
- Verified remote access from SERVER3 using `http://192.168.163.10`
- Confirmed successful client-to-server HTTP connectivity
- ## Implementation Steps

### 1. Installed the IIS Web Server Role

Using Server Manager on SERVER2, I added the Web Server (IIS) role to allow the server to host and serve web content over HTTP.

### 2. Created a Custom Web Page

I created a custom `index.html` file inside the default IIS web root:

`C:\inetpub\wwwroot`

The page contained basic HTML identifying the server as part of my Windows Server lab environment.

### 3. Tested IIS Locally

On SERVER2, I opened Microsoft Edge and navigated to:

`http://localhost`

The custom webpage loaded successfully, confirming that IIS was running and serving the `index.html` file locally.

### 4. Tested IIS From Another Server

From SERVER3, I navigated to:

`http://192.168.163.10`

The custom webpage hosted on SERVER2 loaded successfully.

This verified that SERVER3 could communicate with the IIS web server across the lab network.

## How the Request Works

SERVER3 → HTTP Request → SERVER2 → IIS → index.html → HTTP Response → SERVER3

IIS receives the HTTP request, locates the requested web content in the web root, and returns the webpage to the client.

## What I Learned

This lab helped me understand the difference between installing a server role and verifying that the service actually works.

I learned how IIS serves web content, the purpose of the `wwwroot` directory, how `localhost` refers to the local machine, and how another machine can access a web server using its IP address.
## Lab Evidence



The first screenshot shows the IIS website successfully loading locally on SERVER2 using `http://localhost`.  

The second screenshot shows SERVER3 successfully accessing the IIS website hosted on SERVER2 at `http://192.168.163.10

<img width="1152" height="1536" alt="A73995E4-DC28-4AFD-8A11-2D3AB1E2ACCF" src="https://github.com/user-attachments/assets/3fa9de09-b0ce-4498-9b40-f785fc83ddb4" />
<img width="1152" height="1536" alt="F7CB763F-DB30-4B70-8ED2-505DC5E401D2" src="https://github.com/user-attachments/assets/e2484b8d-8f70-4c72-b7ae-db153ff56cb7" />
successfully accessing the IIS website hosted on SERVER2 at `192.168.163.10`.
