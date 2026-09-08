---
uid: Transcoding
title: Transcoding
legacyUrl: /support/solutions/articles/44001159897-transcoding
redirFromUrl: Transcoding.md
---

Emby can convert your media during playback so that it is compatible with the device you are playing on.
That process is known as transcoding.

In most cases the server and the apps select suitable settings on their own, weighing network performance,
the media's own format, what the device is capable of, and your configuration. Sometimes it is worth
stepping in and configuring things yourself.

Transcoding is only one of three ways Emby can deliver a file, and the cheapest outcome is usually not to
transcode at all - see [Playback Methods](Playback-Methods.md) for the difference between direct play,
direct streaming and transcoding.

## Bitrate

Every Emby app has a "Max streaming bitrate" setting. It is the single most influential setting on the app
side, and it governs image quality directly: raising it improves quality but demands a faster connection
between the device and the server.

Most people get the best results by leaving it on Auto, since Emby apps increasingly detect the achievable
bitrate themselves.

## Formats That Cannot Be Transcoded

Some formats cannot be transcoded at all:

- [DVD and Blu-ray](../../Movie-Naming.md#dvd-and-blu-ray-file-formats)
- [ISOs](../../Movie-Naming.md#iso-format)
- [3D videos](../../3D-Videos.md)

## Configuring Transcoding

How transcoding is performed - which device does the work, which encoders and decoders it uses, and under
what conditions - is set up on the Transcoding page of the server dashboard. See
[Configuration](configuration/Transcoding-Configuration.md) for how that configuration is organised, and
[Settings](Settings.md) for the options that sit alongside it.

If you want the work done by a GPU rather than the CPU, see
[Hardware Acceleration](hardware/Overview.md), and
[GPU Setup](../setup/gpu-setup/GPU-Setup.md) for what has to be installed on the server first.

## When Something Is Wrong

If media is transcoding when you did not expect it to, or transcoding is failing or slow, see
[Troubleshooting](Troubleshooting.md).
