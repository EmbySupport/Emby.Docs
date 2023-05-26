---
uid: Backup
title: Configuration Backup
legacyUrl: /support/solutions/articles/44001159936-configuration-backup
legacyUrl: /support/solutions/articles/44001159936-backup
---

This guide will go over how to migrate your settings from Emby Server from one machine to another. There are two methods to backing up Emby Server settings and we'll go over them here.

## Use the Server Configuration Backup Plugin

We recommend using the Server Configuration Backup plugin, which is designed to make this process really painless by doing the work for you. This plugin requires Emby Premiere and can be found in our plugin catalog.

The Server Configuration Backup plugin can help you backup and restore the following:

* Server configuration
* Users
* User data (play-states, favorites, etc).
* Installed plugins
* Plugin settings
* Playlists

This will not backup library contents and metadata. To keep a permanent copy of metadata, we suggest enabling saving of local metadata to media folders.  The plug-in also does not backup live TV recording settings or series at this time.

## How to use the Server Configuration Backup Plugin
* Be sure your Emby Premiere key is properly installed and validated.  Configuration Backup requires Emby Premiere.
* Install the plugin into your existing Emby Server
* Configure the Backup plugin by setting a folder to save the backups within.
By default, this process will run every 12 hours and will retain at most 3 backups. You can monitor your folder to see that backups are created.
* Install the plugin on your new Emby Server installation, then configure to backup folder to the same parent folder that contains your backups.
* Click on a backup, you'll then be taken to the restore screen where you can run a restore.

ote: if previous backups do not show up correctly, check to make sure you have selected the parent folder and not the specific folder holding the backups.

## How to Restore from a Backup
- Goto Plugins
- Click on the Server Configuration Backup plugin
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

![](images/server/programdatapath.png)

From now on this guide will refer to this path as /ProgramData.

### Review Paths on the Old Setup

Take a look at the configuration on your old server instance. Review any paths you've configured into the server such as cache folders, channel download folders, transcoding folders, as well as any paths configured within plugins. The new server will need to be able to reach these paths, and generally will require write access. If this isn't the case, then various components of the new server may have problems. If you're in doubt, revert these settings to their defaults before proceeding.


### Backup Files

Shutdown the old server instance and backup the following files and directories:
* /ProgramData/config
* /ProgramData/plugins
* /ProgramData/data/collections
* /ProgramData/data/playlists
* /ProgramData/data/displaypreferences.db
* /ProgramData/data/userdata_v2.db (if present)
* /ProgramData/data/users.db

**Note**:  Unless you use a custom Metadata path you will want to backup your /ProgramData/metadata folder to preserve your People images.  The only two folder in metadata you don't need are library and views.

### Install Emby Server on the new machine

Install Emby on the new machine as you normally would. When the startup wizard launches in the browser, do not complete it and instead shut down the server.

Now take all of the files you backed up from the old server and copy them into the equivalent locations on the new server.

Then launch the new server, sign into the dashboard and setup your library paths. Allow the scan to complete as normal.

### After the Scan

If your library was configured with identical paths as the old setup then user data will generally be preserved as well as user library permissions. You may still want to review the library access for each user to ensure their channel and folder access is restricted as desired.
