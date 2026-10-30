---
uid: DirectPlay-Stream-Transcoding
title: Playback Methods
longTitle: Direct Play vs Direct Streaming vs Transcoding
legacyUrl: /support/solutions/articles/44001920144-direct-play-vs-direct-streaming-vs-transcoding
redirFromUrl: DirectPlay-Stream-Transcoding.md
---

Emby can presently deliver your media in one of three ways:

## Direct Play

The media file is used as it is, without modification. It can be sent from Emby Server or, with some clients,
played directly from the file system. The media fits all the criteria needed by the client, including:

- Stored in a compatible [file container](xref:Learn-Containers-and-Codecs) playable by the client
- Encoded with compatible codecs for the client
- Encoded with a compatible bitrate for the client
- Has a resolution compatible with the client

## Direct Stream

Also known as [transmuxing](xref:Learn-Playback-Remuxing). The media file is altered in real time while being
delivered to the client. This happens when the video is compatible but something else needs converting,
such as the container, audio or subtitle track.

In this case the server extracts the video track from the file as well as other tracks it can use. Emby may convert the audio or subtitle tracks on the fly during a Direct Stream.

[Direct Streaming](xref:Learn-Playback-Direct-Stream) does not alter the video tracks in any way, so there is
no loss of video quality. Direct Streaming is not very CPU intensive.

## Transcoding

[Transcoding](xref:Learn-Playback-Transcoding) takes place when the video needs to be converted. This could
be because the video codec isn't supported, the bitrate is higher than the client can use, or subtitles
need to be [burned into the video](xref:Learn-Subtitle-Burn-In).

Transcoding decodes the video, processes it as needed, and encodes it again in a format and at a bitrate
the client app can use.

Transcoding is more CPU intensive than Direct Streaming because it has to decode, process and re-encode
the video. There will be some [loss of video quality](xref:Learn-Video-Generation-Loss) when transcoding takes place.

Emby supports offloading the transcoding process to a GPU.

## Further Reading

<xref:Learn-Playback-Direct-Play>
