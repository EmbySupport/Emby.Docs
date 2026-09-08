---
uid: Server-Transcoding-Settings
title: "Settings"
longTitle: "Transcoding Settings"
---

These options sit on the Settings tab of the Transcoding page and apply to transcoding generally,
independently of which device performs it. Which device does the work, and how, is configured on the
[Transcoding tab](configuration/Transcoding-Configuration.md) instead.

## Transcoding Temporary Path

Transcoding produces temporary files, and this is where they are written. Leaving it unset uses the
server's own default location.

If you set a custom path, make sure that:

- the folder is writable
- the folder is not used for anything else - the server deletes its contents to keep it clean

## Transcoding Throttle

TBA

## Audio Boost

Converting surround audio down to two-channel stereo commonly leaves the result quieter than the original.
The audio boost is a scale factor that compensates for this. The default is **2**, meaning the volume is
doubled when surround is down-mixed to stereo.

## HDR Tone Mapping

Controls whether HDR content is tone mapped for devices that cannot display it, and in which
circumstances - never, only with hardware accelerated transcoding, only with software transcoding, or
either.

TBA

## On-the-Fly Subtitle Extraction

TBA

## On-the-Fly Font Extraction

TBA

## HEVC Encoding

TBA

## Maximum Transcoding Resolution

Caps the resolution transcoded output may have, regardless of the source. The choices are no limit, 4K,
1080p, 720p and 480p.

TBA
