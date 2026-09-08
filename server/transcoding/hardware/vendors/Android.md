---
uid: Server-Hwa-Vendor-Android
title: "Android"
longTitle: "Hardware Acceleration on Android"
legacyUrl: /support/solutions/articles/44001160208-hardware-acceleration-on-android
redirFromUrl: Hardware-Acceleration-on-Android.md
---

MediaCodec is Android's own API for hardware accelerated video decoding and encoding, and it is what Emby
Server uses on Android.

You will also come across OpenMax (OMX), which is an API specification covering several aspects of media
acceleration. On Android it is the standard API for codec *implementations*, while applications reach
those codecs through MediaCodec. This is why codecs are often named something like
`h26x.OMX.Google.encoder.*` - the OMX in the name indicates how the codec is implemented, not how Emby
talks to it.

## GPU Context Types

**MediaCodec** is the only context type on Android.

Note that no curated filter set exists for MediaCodec yet, so filtering options are not offered for this
context the way they are for the desktop backends.

## Hardware Requirements

What is available depends entirely on the device and on what its manufacturer chose to implement. The
number of Android devices makes a compatibility list impractical to maintain, but hardware accelerated
codecs have been successfully tested with silicon from:

<!-- REVIEW: list of tested manufacturers carried over from the previous article, not verified -->


- Nvidia (Tegra)
- Samsung (Exynos)
- AmLogic
- RealTek

That is not a guarantee for every device from those manufacturers.

## Drivers

No setup or driver installation is required. Emby detects the available hardware codecs automatically.

## What Your Device Can Do

The codecs detected for your device are shown in the transcoding configuration - see
[Advanced Mode](../../configuration/Advanced-Mode.md).
