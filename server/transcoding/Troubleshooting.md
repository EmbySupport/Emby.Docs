---
uid: Server-Transcoding-Troubleshooting
title: "Transcoding Troubleshooting"
---

# Transcoding Troubleshooting

## Why Is My Media Transcoding?

If the question is why transcoding is happening at all, rather than why it is failing or slow, see
[Why Is My Media Transcoding?](Why-Media-Transcodes.md).

## High CPU Usage Despite Hardware Acceleration

The most common cause is subtitle burn-in. PGS and DVD subtitles frequently have to be burned into the
video during transcoding, and most GPUs cannot do this, so the CPU ends up heavily involved. It is a
taxing process even for a powerful server, and worth avoiding:

- Turn subtitles off before playback, using the pre-playback subtitle selection menu
- Use external text-based subtitles such as `.srt` instead. Emby Server's subtitle download features can
  automate acquiring them
- Use an Emby app that can direct play these subtitle formats without transcoding, such as Emby Windows,
  Emby Linux, Emby for macOS, Android or iOS

## Hardware Acceleration Fails with Remote Desktop

See [Hardware Acceleration fails with RDP](Hwa-Fails-with-RDP.md).

