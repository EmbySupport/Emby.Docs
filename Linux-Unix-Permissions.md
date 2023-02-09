---
uid: Linux-Unix-Permissions
title: Linux/Unix Permissions
legacyUrl: /support/solutions/articles/44001962818-linux-unix-permissions
---

Excellent advice from user Q-Droid on the Emby Forums



This is an excerpt from a community thread by a member who wanted to allow other applications and Linux users on their server to access the media structure used by Emby. The member wanted shared read and write access to the libraries which may contain files and directories owned by different users.



1. Allow group of users (my-user,Emby,Kodi,etc.) to read and write media content.
2. Allow same for SMB shares.



Generally speaking you can't prevent Emby from following the rules of the OS and in Linux/UNIX these rules were created for security reasons. A "line of code" won't change that because only the superuser is allowed to change ownership at the user level. Emby doesn't run as superuser and you really don't want to do that anyway. So instead you work with the rules and tools for the OS.

There are multiple ways to do this, I'll share what I would do. Need elevated rights for this, i.e. root.

Identify your media base directory. Usually it's the common starting directory for your libraries. For example, if your libraries look like this:


```<language>
/mnt/library/movies
/mnt/library/tv shows
/mnt/library/music
```


Then "/mnt/library" is your base. Servers with multiple storage volumes and external drives can have multiple paths to the libraries without a common base. If this is the case then modify each library path individually and pick a directory from which subdirectories will be created, but not "/" and not "/mnt".



On the Emby server with the media to be shared, create a group for media if it doesn't exist. The group name is arbitrary though it helps to be descriptive:
groupadd media



Add members to the group (my-user, emby, etc.):
usermod -a -G media my-user
usermod -a -G media emby
...

We'll use ACLs. First to set the permissions and then to set the defaults. It can be done in one command but it's easier to follow this way. Members of the media group will be able to access and modify files and directories under /mnt/library. New files and directories will be created with permissions for the media group.



Set permissions for media group on existing items (the 'X' is upper case):
setfacl -R -m g:media:rwX /mnt/library



Define default permissions for media group. Applies to new items:
setfacl -R -m d:g:media:rwX /mnt/library
 

If you're using SMB/CIFS you can enforce similar rules. Assuming the users are the same and the group can be added.

In smb.conf and for each of the shares add to current config:
[share name]
create mask = 0664
directory mask = 0775
force group = media

The above should give you enough information to get started with minimal tweaking needed.