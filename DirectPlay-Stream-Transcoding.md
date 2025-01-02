---
uid: DirectPlay-Stream-Transcoding
title: Playback Methods
longTitle: Direct Play vs Direct Streaming vs Transcoding
legacyUrl: /support/solutions/articles/44001920144-direct-play-vs-direct-streaming-vs-transcoding
---

Emby can presently deliver your media in one of three ways:

## Direct Play
Media file is used AS IS without any modification.  It can be sent from the Emby server or (some clients) allowed to be played directly from the file system. The media fits all the criteria needed by the client including:

* Stored in a compatible file container playable by the client
* Encoded with compatible codecs for the client
* Encoded with a compatible bit rate for the client
* Has a resolution compatible with the client

## Direct Stream
Also known as transmuxing. The Media file is altered in real-time while being delivered to the client. This happens when the video codec is correct but something else needs converting like the streaming type (package), audio or subtitle track.

In this case the server extracts the video track from the file as well as other tracks it can use. Emby may convert the audio or subtitle tracks on the fly during a Direct Stream.

Direct Streaming does not touch the video tracks in anyway so there is no loss of video quality. Direct Streaming is not very CPU intensive.

## Transcoding
Transcoding takes place when the video needs to be converted.  This could be because the video codec isn't support, the bitrate of the video is higher than the client can use, a subtitle needs to be "burnt" into the video.

Transcoding at a high level, is taking already encoded content; decoding it; and then altering it. After altering, it is then reassembled/encoded back into a format compatible with the client app using the proper bitrate and a format the client app can use.

Transcoding is more CPU intensive then Direct Streaming due to having to decode/alter/recode the video.   There will be some loss of video quality when transcoding takes place.

Emby supports offloading the transcoding process to a GPU


