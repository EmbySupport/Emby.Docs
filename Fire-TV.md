Emby for Fire TV can be installed from the App store on your Fire TV device (Fire TV 1st or 2nd gen or Fire TV Stick) or you can push it to your device from the [Amazon Store](http://www.amazon.com/Emby-for-Fire-TV/dp/B00VVJKTW8?ie=UTF8&keywords=emby&qid=1459793610&ref_=sr_1_1&sr=8-1).


Emby for Fire TV can handle just about any type of media thanks to Emby Server transcoding. If you would like to learn how to prepare your media for Direct Play, read below.

## Setup Guide
Install the app using one of the above methods, the app will then automatically find your local Emby Server(s).  If it cannot find your server or you are attempting to connect to a remote server, the app will present you with options to connect manually or use Emby Connect.

## Direct Play Media Formats
Video — m4v,mov,xvid,vob,mkv,wmv,asf,ogm,ogv,mp4,webm Note: The exact containers and codecs that will direct play depends on both the exact version of Fire TV and the audio equipment it is connected to (and the type of connection - e.g. HDMI, optical, etc.). 
Subtitles - srt,vobsub,ssa,pgs,pgssub,ass,sub,vtt 
Audio – flac,aac,mp3,mpa,wav,wma,mp2,ogg,oga,webma,ape,ac3 (Dolby Digital)
## Best Practices for Direct Play
Ensure your media meets the above criteria.

Leave the app's streaming bitrate setting on the default value of Auto, if possible. The app will perform bandwidth tests with your Emby Server to determine the maximum playable bitrate.

If you are customizing the bitrate setting, then you will need to compare the bitrate of your files to the bitrate setting in the app. You can find the bitrate of a file by checking the media info in the web interface. If the bitrate of a file is higher than the setting in the app, transcoding will be required. Increasing the bitrate setting in the app can help reduce transcoding, but may impact playback performance if your network connection is not fast enough to handle it.