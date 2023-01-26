Requires Android TV 5.1 on higher OS.

Emby for Android TV can be installed from the App store on your Android TV device (Google Nexus Player, Nvidia Shield, Sony Android TV, etc.) or you can push it to your device from the [Google Play Store](https://play.google.com/store/apps/details?id=tv.emby.embyatv).


Emby for Android TV can handle just about any type of media thanks to Emby Server transcoding. If you would like to learn how to prepare your media for Direct Play, read below.

## Setup Guide
Install the app using one of the above methods, the app will then automatically find your local Emby Server(s).  If it cannot find your server or you are attempting to connect to a remote server, the app will present you with options to connect manually or use Emby Connect.

## Direct Play Media Formats
Video — m4v,mov,xvid,vob,mkv,wmv,asf,ogm,ogv,mp4,webm 
Note: The exact containers and codecs that will direct play depends on both the device the app is on and the audio equipment it is connected to (and the type of connection - e.g. HDMI, optical, etc.).  The device with the widest support is the NVidia Shield.  
Subtitles - srt,dvdsub,ssa,ass,sub,vtt,pgs  
Audio – aac,mp3,mpa,wav,wma,mp2,ogg,oga,webma,ape,opus,ac3 (Dolby Digital), DTS, DTS-HD MA, TrueHD  

*Dolby Digital and DTS direct play requres Android version 6.0+*  

*DTS HD and TrueHD require compatible hardware (Nvidia Shield)*  

## Best Practices for Direct Play 
Ensure your media meets the above criteria.

Leave the app's streaming bitrate setting on the default value of Auto, if possible. The app will perform bandwidth tests with your Emby Server to determine the maximum playable bitrate.

If you are customizing the bitrate setting, then you will need to compare the bitrate of your files to the bitrate setting in the app. You can find the bitrate of a file by checking the media info in the web interface. If the bitrate of a file is higher than the setting in the app, transcoding will be required. Increasing the bitrate setting in the app can help reduce transcoding, but may impact playback performance if your network connection is not fast enough to handle it.