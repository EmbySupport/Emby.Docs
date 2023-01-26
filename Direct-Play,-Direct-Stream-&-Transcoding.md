Emby can presently deliver your media in one of three ways:

## Direct Play
Media file is used AS IS without any modification.  It can be sent from the Emby server or (some clients) allowed to be played directly from the file system. The media fits all the criteria needed by the client including:

* Stored in a compatible file container playable by the client
* Encoded with compatible codecs for the client
* Encoded with a compatible bit rate for the client
* Has a resolution compatible with the client

## Direct Stream
Also known as transmuxing. The Media file is altered in real-time while being delivered to the client.  This happens when the container of the media file is not compatible with the client, (.avi, .wmv, .ts, etc), but the resolution, bitrate, and codecs are supported.

In this case the server extracts the internal tracks of the media file such as the video, audio & subtitle tracks and rewrites the file in real-time to a compatible container format the client does support.

Direct Streaming does not touch the video or audio tracks in anyway so there is no loss of quality.

## Transcoding
Transcoding takes place when one or more tracks in the media file are not compatible with the client app.  This could be the video codec, audio codec, or subtitle being used. The media file could have a higher resolution then requested by the client app or the bit rate of the file could be higher then the client can presently use.

Transcoding at a high level, is taking already encoded content; decoding it; and then altering it.  After altering, it is then reassembled/encoded back into a format compatible with the client app and the current settings it is using.

As an example, you might change the audio and/or video format (codec) from one to another, such as converting from an MPEG2 source (commonly used in broadcast television) to H.264 video and AAC audio (the most popular codecs for streaming).

Transcoding only the audio track is a light weight process.
Transcoding video can be very taxing on the CPU in the server depending on the resolution, bitrate and codecs being used.

Emby supports offloading the transcoding process to a [GPU](Hardware-Acceleration-Overview)


