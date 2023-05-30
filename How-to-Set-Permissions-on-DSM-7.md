---
uid: How-to-Set-Permissions-on-DSM-7
title: How to Set Permissions on DSM 7
legacyUrl: /solutions/articles/44002313183/
---
## How to Set Permissions on DSM 7
For Synology versions of DSM 7 and higher you need to assign read or read/write permissions to the system internal emby user for any directories used by Emby such as your media folders. We recommend setting read/write permissions to take full advantage of Emby's features.

To set permission open the Control Panel on Synology DSM.  Then open Shared Folders.
Highlight the shared folder containing the media you wish to appear in Emby.
![synology-permissions1.png](images/synology/synology-permissions1.png)
Click Edit, then select the Permissions tab:
![synology-permissions2.png](images/synology/synology-permissions2.png)

Change the drop down user type to "System internal user" (in the red box above).
Scroll down if needed until you see the emby user.
Check the column to give emby at least Read Only access but we suggest granting Read/Write access like this:

![synology-permissions3.png](images/synology/synology-permissions3.png)

Click the Save button.
Repeat this process for any other shares containing media for Emby.
Emby Server should now be able to access all shares you have updated.
