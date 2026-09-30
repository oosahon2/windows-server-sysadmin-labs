# NTFS and Share Permissions Lab

## Overview

In this lab, I configured NTFS and share permissions for a shared folder on Windows Server. I used an Active Directory security group to control access and tested the permissions from a separate domain-joined server.

## Lab Environment

- Virtualization Platform: VMware Workstation
- Domain: bobby.local
- File Server: SERVER3
- Client/Test Server: SERVER4
- Shared Folder: DepartmentFiles
- Security Group: Finance-Users
- Operating System: Windows Server

## Objectives

- Create a folder for departmental files
- Configure NTFS permissions
- Assign permissions using an Active Directory security group
- Configure SMB share permissions
- Access the shared folder from another server
- Test create, write, and delete permissions

## NTFS Permissions

I added the **Finance-Users** Active Directory security group to the DepartmentFiles folder.

The group was assigned **Modify** permission.

Modify permission allows authorized users to:

- Read files and folders
- Create files and folders
- Edit existing files
- Delete files and folders

## Share Permissions

The DepartmentFiles folder was shared over the network.

Share permissions were configured with:

- Everyone: Full Control

NTFS permissions were then used to control the actual level of access for users and groups.

## Testing

From SERVER4, I connected to the shared folder using:

`\\SERVER3\DepartmentFiles`

I tested the permissions by:

1. Accessing the shared folder from SERVER4
2. Creating Finance-Test.txt
3. Adding text to the file
4. Saving the file
5. Deleting the file

All tests completed successfully.

## Key Concepts Learned

- NTFS permissions control access to files and folders stored on an NTFS volume.
- Share permissions apply when a folder is accessed over the network.
- NTFS and share permissions work together for network access.
- Active Directory security groups can be used to manage permissions instead of assigning permissions individually to users.
- Modify permission allows users to read, create, edit, and delete files.
- Using groups makes permission management easier and more scalable.

## Result

The NTFS and SMB share permissions were successfully configured and tested. A member of the authorized group was able to access the shared folder from SERVER4 and create, modify, save, and delete a file stored on SERVER3.
