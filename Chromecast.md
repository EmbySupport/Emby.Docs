Emby supports casting to Chromecast in the following apps:

- [Android Mobile (Google Play)](https://play.google.com/store/apps/details?id=com.mb.android "Android Mobile (Play Store)")
- [iPad](https://itunes.apple.com/us/app/emby/id992180193?ls=1&mt=8 "iPad")
- [iPhone](https://itunes.apple.com/us/app/emby/id992180193?ls=1&mt=8 "iPhone")
- [Web App (Chrome only)](http://app.emby.media)
- Local Web App (Chrome only)

To connect to your Chromecast device, simply click the cast icon in the top right corner of the app. You'll then be asked which device you'd like to connect to.

Emby for Chromecast can handle just about any type of media thanks to [Emby Server transcoding](Transcoding). If you would like to learn how to prepare your media for Direct Play, read below.

# Direct Play Media Formats

* Video — MP4, M4V, MKV, WEBM
* Subtitles - SRT and other text-based formats
* Audio – AAC, MP3, WAV, FLAC, OPUS

* FLAC is currently only supported by Chromecast Audio devices. All other Chromecast devices can play FLAC using Emby Server transcoding.

# Best Practices for Direct Play

* Ensure your media meets the above criteria.

* Leave the casting app's Chromecast streaming bitrate setting on the default value of Auto, if possible. The app will perform bandwidth tests with your Emby Server to determine the maximum playable bitrate.

* If you are customizing the bitrate setting, then you will need to compare the bitrate of your files to the bitrate setting in the app. You can find the bitrate of a file by checking the media info in the web interface. If the bitrate of a file is higher than the setting in the app, transcoding will be required. Increasing the bitrate setting in the app can help reduce transcoding, but may impact playback performance if your network connection is not fast enough to handle it.