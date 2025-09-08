---
uid: Server-Data-Folder
title: Emby Server Data Folder
---

## Emby Server Data Folder

The Emby Server data folder can generally be located in one of the following locations, depending on the server platform. If your server is running, then The location can also be found on the Emby Server Dashboard by clicking the 3-dot menu, and then "Get Server Info".

For NAS platforms, tools like [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and [WinSCP](https://winscp.net/eng/download.php) can be used to access the Emby Server Data Folder area, once SSH has been enabled on ths NAS.

### Windows
C:\Users\\{user}\AppData\Roaming\Emby-Server

### macOS
/Users/{user}/emby-server

or

/Users/{user}/.config/emby-server

### Android
/storage/emulated/0/Android/data/com.emby.embyserver/files
 
See this NVIDIA Shield article for how to access this area from a PC:
https://nvidia.custhelp.com/app/answers/detail/a_id/4172/~/how-do-i-share-shield-tv-folders-with-a-pc

### Linux
/var/lib/emby

### Asustor
/home/emby
 
Accessing this folder directly will require SSH. See the SSH section within an ASUSTOR course here:
https://www.asustor.com/en/online/College_topic?topic=109#lux5

### Synology
/volume1/@appdata/EmbyServer

Accessing this folder directly will require SSH. Check out our SSH Tutorial with examples here:
https://emby.media/community/index.php?/topic/118986-tutorial-ssh-into-synology-nas-with-useful-examples/

### QNAP
/share/CACHEDEV1_DATA/.qpkg/EmbyServer/programdata

or

/share/HDA_DATA/.qpkg/EmbyServer/programdata

or

/share/ZFSxxx_DATA/.qpkg/EmbyServer/programdata

Path Example for QuTS Hero:

/share/ZFS530_DATA/.qpkg/EmbyServer/programdata

Accessing this folder directly will require SSH.

### TerraMaster
/home/emby

Accessing this folder directly will require SSH.

### Western Digital
/mnt/HD/HD_a2/emby

Accessing this folder directly will require SSH.
