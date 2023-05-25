---
uid: Emby-Server-does-not-start---Security-advisory-2023-05-25
title: Emby Server does not start - Security advisory 2023-05-25
---

# Abstract

## Applicability

This article applies to cases where you are experiencing one or more of the following symptoms:

- Your Emby Server has shut down and will not start effective 2023-05-25
- You encounter a message in the Emby Server log file starting with "We have detected a malicious plugin on your system which has probably been installed without your knowledge."
- You encounter an error entry in the Windows event log, Source=".NET Runtime", EventId=1025 with the same text as above in the event details
## Background

Starting Mid-May 2023, it was discovered a hacker(s) had managed to use a "Proxy Header Vulnerability" to infiltrate Emby Servers improperly configured for remote access, gaining admin access with ability to install a custom plugin. Note: Emby Server version 4.8 (beta) already contains fixes that would have prevented this.

After careful analysis and evaluation of possible mitigation strategies, the Emby team was able to push out updates to Emby Server instances which enabled detection of the custom plugin used by the exploit and prevent it from running.

The Emby team determined that shutting down the server and preventing further startup up as the most suitable action as it disables the plug-in and draws the attention of the administrator to find out why the server isn't running.

## Risk and Impact

It is best to assume a positive detection of intrusion has allowed access to Emby Server configuration data as well as system data available to the operating system account used to run Emby Server.


## Actions to Take

- Remove any plug-in named helper.dll or EmbyHelper.dll
             Primary location is the plugins folder under Emby's programdata folder
             Also look in cache and data subfolders
- Add an entry to your etc/hosts file:

             emmm.spxaebjhxtmddsri.xyz 127.0.0.1

  Note: This is the host name of the control server which the malware is communicating with
- Change the password of the OS system account running Emby Server
- Run a complete Malware and Virus scan on the full system.
- Check the OS itself for
             Suspicious user accounts
             Unknown processes
             Unknown network connections and open ports
             SSH configuration changes if applicable
             Firewall rule changes

## Getting Emby Server to Start Again

After (and only after) you have done the above:
- Disable your router's port forwarding rule used for remote access to the Emby Server
- Go to the following folder under the emby programdata folder:

  programdata/plugins/configurations

 - Delete the file named ReadyState.xml.
 - Delete the file named 'EmbyScripterX.xml' (if exists)

- **Update Emby Server to 4.7.12 or newer. Beta Servers use version 4.8.0.31 or newer.**
- Start Emby Server
- Assign new passwords to all accounts.
- Set all admin accounts to use "Require a password on the local network". Best to configure all accounts this way.
- Configure admin accounts to "Hide this user from login screens on the local network" as well as "Hide this user from login screens when connected remotely".
- Consider setting up non admins accounts to use "Hide this user from login screens on devices they've never signed into".
- Tighten security as much as possible, especially network settings.
- Enable your router's port forwarding rule used for remote access to the Emby Server


