---
uid: Emby-Server-does-not-start---Security-advisory-2023-05-25
title: Emby Server does not start - Security advisory 2023-05-25
---

# Abstract

## Applicability

This article applies to cases where you are experiencing one or more of the following symptoms:

- Your Emby Server has shut itself down and/or does not start anymore since 2023-05-25
- You encounter the following message in the Emby Server log:
  _We have detected a malicious plugin on your system which has probably been installed without your knowledge. Please see https://emby.media/support/articles/advisory-23-05.html for more information on how to proceed. For your safety we have shutdown your Emby Server as a precautionary measure_ **Note: Your server was never directly accessed by us. We used our standard update mechanism**
- On Windows installs, you encounter an error entry in the Windows event log, `Source=".NET Runtime", EventId=1025` with the same text as above in the event details

## Background

Starting Mid-May 2023, a hacker managed to infiltrate private user-hosted instances of Emby Server which were accessible via public internet and had an insecure configuration for administrative user accounts. Combined with the "Proxy Header Vulnerability", which was recently fixed in the beta channel, this allowed an attacker to gain administrative access on such systems.
Eventually, this allowed the attackers to install a custom plugin of their own, which establishes a backdoor in the running process of Emby Server.

After careful analysis and evaluation of possible strategies for mitigation, the Emby team was able to push out an update to Emby Server instances which is able to detect the plugin in question and prevents it from being loaded. Due to the severity and the nature of this situation and in an abundance of caution we are preventing affected servers to start up again after the detection. As the given situation requires direct action and assessment by the administrator, we determined that shutting down the server and preventing further startup up is the most suitable action as it disables the plug-in, possibly prevents the situation from getting worse and at the same time draws the attention of the administrator onto the subject.

Analysis of the plug-in has revealed that it is forwarding the private Emby Server login credentials including the password for every successful login to an external server under control of the hackers.

## Actions to Take

- Delete the plugin .dll file, which comes as `helper.dll` and `EmbyHelper.dll`
  - Primary location is the `plugins` folder under Emby's `programdata` folder
  - Also look in `cache` and `data` subfolders
- Add an entry to your server machine etc/hosts file:
             emmm.spxaebjhxtmddsri.xyz    127.0.0.1
             This is the host name of the control server which the malware is communicating with

Review your server machine for:

- Suspicious user accounts
- Unknown processes
- Unknown network connections and open ports
- SSH configuration
- Firewall rules
- Change all passwords

## Starting Emby Server

After (and only after) you have done the above:

- Disable external network access 
- Go to the following folder under the [Emby Server Data Folder](Server-Data-Folder.md):
  `programdata/plugins/configurations`
  - Find the file named `ReadyState.xml` and delete it.
  - Find the file named 'EmbyScripterX.xml' and delete it (if exists)
- Start Emby Server
- Assign new passwords to all of your Emby Server users
- Don't allow local login without password
- Ensure no user has an empty password
- Re-Enable public network access
  - Consider changing IP address, port, or DNS name  (whatever applicable)

## Install Emby Server 4.7.12 Security Update

- Watch out for this update and install as soon as it becomes available


