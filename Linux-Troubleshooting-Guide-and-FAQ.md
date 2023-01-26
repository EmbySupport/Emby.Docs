#### Emby Server does not restart from the web interface:
Emby on Linux does not have the built-in capability to restart itself. So to restart Emby uses a helper script. The helper script named ```restart.sh``` can be found on most distributions at ```/usr/lib/emby-server```. The script can only restart Emby if it was started by a service manager program such as systemctl or service. If for some reason the helper script does not successfully restart Emby for you, please check the following:
* Ensure helper script is executable.
* Ensure Emby was started via a service manager.
* Ensure permissions of /etc/sudoers.d/emby are 0640
* Ensure whatever user is running emby-server is part of the emby group (usermod -a -G emby $USER_NAME)
* Ensure /etc/sudoers permissions is 0640

####Example of troubleshooting restart on a distribution using systemd:

1. ```sudo systemctl status emby-server``` - Get PID.
2. Hit restart on web interface
3. ```sudo systemctl status emby-server``` - Get PID.

If PIDs differ restart was successful. Otherwise, check the following:

1. ```ls -la /usr/lib/emby-server/restart.sh``` - ensure it is executable.
2. ```ps -aux | grep emby``` - Take note of PID
3. ```sudo -u emby /usr/lib/emby-server/restart.sh``` - if you are running emby-server as another user other than emby, please adjust command appropriately.
4. ```ps -aux | grep emby``` - Take note of PID

If PIDs differ restart worked.

