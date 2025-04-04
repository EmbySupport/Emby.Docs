---
uid: Linux
title: Linux
legacyUrl: /support/solutions/articles/44002311270-linux
---

### Installation:

Emby-Server is packaged and supported on as many platforms and architectures as possible. You can find installation instructions that are distribution specific either [here](Installation.md) or on our [Downloads page](https://emby.media/download). Additionally, you can find our official docker images on the [hub](https://emby.media/docker-server.html) which support armv7l and amd64.

### Before running the Wizard:

Ideally before running the setup wizard you might want to setup Emby-Server or your media files with the appropriate permissions. Permission on Linux are very important and if they are not set correctly on your media folders or Emby-Server's configuration folder, your experience maybe be sub-par. By default, Emby-Server runs under the user `emby`. It is highly unlikely that user `emby` will have read and write permissions to your media directories. This  issue can be addressed in one of two ways. One, you can adjust the user Emby server runs as. You can do this by adjusting the conf file which can be found in `/etc/emby-server.conf`. Please read the comments and directions within the file. Or secondly, you can append the user emby to the group that has read and write access to your media files. You may read more about Linux permissions [here](https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions).
