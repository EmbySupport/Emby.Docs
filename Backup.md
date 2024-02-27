---
uid: Backup
title: Configuration Backup
legacyUrl: /support/solutions/articles/44001159936-configuration-backup
legacyUrl: /support/solutions/articles/44001159936-backup
---

This guide will go over how to migrate your settings from Emby Server from one machine to another. There are two methods to backing up Emby Server settings and we'll go over them here.

## Use the Backup & Restore Plugin

We recommend using the Backup & Restore plugin, which is designed to make this process really painless by doing the work for you. This plugin requires Emby Premiere and can be found in our plugin catalog.

The Backup & Restore plugin can help you backup and restore the following:

* Server configuration
* Users
* User data (play-states, favorites, etc).
* Installed plugins
* Plugin settings
* Playlists

This will not backup library contents and metadata. To keep a permanent copy of metadata, we suggest enabling saving of local metadata to media folders.  The plug-in also does not backup live TV recording settings or series at this time.

## How to use the Backup & Restore Plugin
* Be sure your Emby Premiere key is properly installed and validated.  Backup & Restore requires Emby Premiere.
* Install the plugin into your existing Emby Server
* Configure the Backup plugin by setting a folder to save the backups within.
By default, this process will run every 12 hours and will retain at most 3 backups. You can monitor your folder to see that backups are created.
* Install the plugin on your new Emby Server installation, then configure to backup folder to the same parent folder that contains your backups.
* Click on a backup, you'll then be taken to the restore screen where you can run a restore.

ote: if previous backups do not show up correctly, check to make sure you have selected the parent folder and not the specific folder holding the backups.

## How to Restore from a Backup
- Goto Plugins
- Click on the Backup & Restore plugin
- This is the configuration screen that will also show you current backups
- Scroll down to "Current Backup"
- Click on the Backup that you wish to restore.
- You will get a screen that gives you options of things that can be - restored.
- You can optionally do restores of only certain parts of the system or for  -only specific users.  Configure as needed.
- Click the "Restore Now" button.
- You're done !

If you prefer to backup manually, read on....

## How to Backup Manually

The following instructions will detail how to manually backup or migrate an Emby Server installation.

### Locate Emby's program data folder

The path to the [Emby Server Data Folder](Server-Data-Folder.md) can be found in your Emby Server Dashboard by clicking the 3-dot menu next to the server name.
![image](https://github.com/EmbySupport/Emby.Docs/assets/10695413/869368a5-6154-41f0-afe3-cfb8afc1b27f)

Click the view server info menu choice

![image](https://github.com/EmbySupport/Emby.Docs/assets/10695413/a5f23826-d1d0-4901-8fbf-ebbd667234a8)

The top entry shows the parent location for Emby Server.

From now on this guide will refer to this path as /ProgramData.
Simply backup everything in and below /ProgramData using any tool you wish or copy all files to a backup location.

### Migrate to a new server

If you are migrating to a different operating system care should be care should be used to make sure you match up directories properly during the restore as the directory names and locations could be different.

 - Get a good backup as explaned above from you existing system (old).
 - Install the same version number of Emby Server to the computer about to become your (new) system.
 - After running through the setup wizard, shut down Emby Server
 - If space allows, make a copy of the installation to another location on disk. This is only needed if you need to check/fix access rights.
 - Restore the backup from your old machine right over the current installation on the new system.
 - Compare each folder's access rights on the new machine restore to the fresh installation copy.
 - Adjust access rights as needed so they match
 - Start Emby Server.
 - Make any adjustments to file location you may need to make.
 - Run a full library scan on all libraries.
 - Review log files for any errors generated.

### After the Scan

If your library was configured with identical paths as the old setup then user data will generally be preserved as well as user library permissions. You may still want to review the library access for each user to ensure their channel and folder access is restricted as desired.
