---
description: >-
  Anything related to Microsoft Office, either the local apps, or the cloud 365
  apps, or administration of it.
---

# Microsoft Office

## Making an AzureAD user a local admin

1. Login to the PC as the Azure AD user you want to be a local admin. This gets

   the GUID onto the PC.

2. Log out as that user and login as a local admin user.
3. Open a command prompt as Administrator and using the command line, add the

   user to the administrators group:

   `net localgroup administrators AzureAD\JohnDoe /add`

Source: [https://superuser.com/questions/982336/](https://superuser.com/questions/982336/how-do-i-add-azure-active-directory-user-to-local-administrators-group)

## Create a Skype for Business meeting without installing Skype for Business on the local machine

Go to [https://sched.lync.com/](https://sched.lync.com/). You must install a browser plugin when opening the meeting link.

