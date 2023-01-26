You can access Emby Server Log files from the dashboard UI by navigating to **Logs** under the Expert menu.  You will see a list of log files on the right.  Click on one to open it in the web browser.

The physical location of log files is displayed on the dashboard main page in the **Paths** section.

## Log Rollover
By default, Emby Server will start a new log file every day at midnight. The current log file will be renamed and postfixed by a timestamp value.

You can control log rollover through in the Scheduled Tasks section by modifying the execution schedule of the **Rotate Logfile** task

## Log file types

There are three types of log files:
- EmbyServer_xxxxx.txt  
The main server log file, rotated as described above
* ffmpeg_xxxx.txt  
Transcoding logs created for each transcoding or remuxing operation
* hwdetect_xxxxx.txt  
Hardware detection log. Created on every startup of Emby Server

## Fail2Ban Support

Emby Server creates log entries for authentication failures that are compatible with Fail2Ban:
The schema is:

```
AUTH-ERROR: {0} - {1}
```
where {0} is the source IP address and {1} is the error message.


For example:
```
2018-12-28 00:00:00.007 Error AUTH-ERROR: 1.1.1.1 - Invalid username or password entered.
```
