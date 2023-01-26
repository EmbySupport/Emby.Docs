The Emby Web App is the main interface between you and your Emby Server, allowing you to manage server settings, share content with friends and view media content.

# Setup Guide
The Emby Web App is included with your installation of Emby Server. 

To access it just open a web browser and visit: http://{your server ip}:8086.  

# Server Management
The Emby Web App is a convenient place to manage all aspects of your Emby Server, including the [Library](Library Setup), [Users](Users), [Dlna](Dlna Server), [Plugins](Plugins), and more.

# Chromecast and Remote Control
The Emby Web App supports casting to [Chromecast](Chromecast) devices and other Emby apps. To connect to your Chromecast device, simply click the cast icon in the top right corner of the app. You'll then be asked which device you'd like to connect to.
Once connected, any content you play will be sent to the Chromecast device. You're able to play individual files, entire folders, shuffle, instant mix, queue, and more. For more information, see [Chromecast](Chromecast).

# Direct Play Media Formats
The Emby Web app can direct play media to your browser when the browser supports the format natively. Please check your web browser of choice for it's supported media formats.

# Best Practices for Direct Play
Leave the app's streaming bitrate setting on the default value of Auto, if possible. The app will perform bandwidth tests with your Emby Server to determine the maximum playable bitrate.

If you are customizing the bitrate setting, then you will need to compare the bitrate of your files to the bitrate setting in the app. You can find the bitrate of a file by checking the media info in the web interface. If the bitrate of a file is higher than the setting in the app, transcoding will be required. Increasing the bitrate setting in the app can help reduce transcoding, but may impact playback performance if your network connection is not fast enough to handle it.