---
uid: Server-Transcoding-Encoders-MediaCodec
title: "MediaCodec"
longTitle: "MediaCodec Encoder Parameters"
---

On Android, Emby encodes through [MediaCodec](xref:Learn-Hardware-Android-MediaCodec), using the encoders
the device's manufacturer provides. These parameters apply to the encoders of the MediaCodec context type -
see [Android](../../hardware/vendors/Android.md) for the context type, and [Encoders](Encoders.md) for how
the dialog works. Which bitrate modes an encoder supports depends on the device's MediaCodec
implementation. In all three encoders, the bitrate Emby requests is passed as the target and maximum rate,
with a buffer of twice the bitrate.

## H.264

The `h264_mediacodec` encoder for [H.264](xref:Learn-Video-Codec-H264), offered by the MediaCodec context
type.

**Bitrate Mode** - how the device's encoder reaches the bitrate Emby requests (ffmpeg `bitrate_mode`).
Default: **Auto (driver default)**.

- **Auto (driver default)** - sets no mode, so the device uses its own default. The recommended starting
  point
- **Constant Quality** - targets a consistent per-frame quality level instead of a specific bitrate, so the
  output size varies with scene complexity ([constant quality](xref:Learn-Video-Encoding-Constant-Quality))
- **Variable Bitrate (VBR)** - targets an average bitrate and lets it vary with scene complexity
  ([VBR](xref:Learn-Video-Encoding-VBR)). A common general-purpose choice
- **Constant Bitrate (CBR)** - holds the bitrate as close to constant as possible, regardless of scene
  complexity ([CBR](xref:Learn-Video-Encoding-CBR)). Useful for strict bandwidth limits
- **Constant Bitrate with Frame Drops** - like Constant Bitrate, but the device may drop frames to hold the
  bitrate. Gives a harder bitrate guarantee, but can cause visible stutter in sustained complex scenes

**Encoding Profile Limit** - the highest H.264 profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Constrained Baseline Profile**, **Baseline Profile**, **Main Profile**, **Extended Profile**,
**Constrained High Profile**, **High Profile**, **High 10 Profile**, **High 4:2:2 Profile** and
**High 4:4:4 Predictive Profile** that the device's encoder reports.

## HEVC

The `hevc_mediacodec` encoder for [HEVC](xref:Learn-Video-Codec-HEVC), offered by the MediaCodec context
type.

**Bitrate Mode** - how the device's encoder reaches the bitrate Emby requests (ffmpeg `bitrate_mode`).
There is no automatic choice for this encoder; a mode is always passed. Default: **Variable Bitrate
(VBR)**.

- **Constant Quality** - targets a consistent per-frame quality level instead of a specific bitrate, so the
  output size varies with scene complexity
- **Variable Bitrate (VBR)** - targets an average bitrate and lets it vary with scene complexity. A common
  general-purpose choice
- **Constant Bitrate (CBR)** - holds the bitrate as close to constant as possible, regardless of scene
  complexity. Useful for strict bandwidth limits
- **Constant Bitrate with Frame Drops** - like Constant Bitrate, but the device may drop frames to hold the
  bitrate. Gives a harder bitrate guarantee, but can cause visible stutter in sustained complex scenes

**Encoding Profile Limit** - the highest HEVC profile that may be used; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Main Profile**, **Main 10 Profile** and **Range Extension (REXT)** that the device's encoder reports.
Emby does not pass a profile to this encoder, so the limit only decides whether this device entry is used
for a transcode.

## AV1

The `av1_mediacodec` encoder for [AV1](xref:Learn-Video-Codec-AV1), offered by the MediaCodec context
type.

**Bitrate Mode** - how the device's encoder reaches the bitrate Emby requests (ffmpeg `bitrate_mode`).
There is no automatic choice for this encoder; a mode is always passed. Default: **Variable Bitrate
(VBR)**.

- **Constant Quality** - targets a consistent per-frame quality level instead of a specific bitrate, so the
  output size varies with scene complexity
- **Variable Bitrate (VBR)** - targets an average bitrate and lets it vary with scene complexity. A common
  general-purpose choice
- **Constant Bitrate (CBR)** - holds the bitrate as close to constant as possible, regardless of scene
  complexity. Useful for strict bandwidth limits
- **Constant Bitrate with Frame Drops** - like Constant Bitrate, but the device may drop frames to hold the
  bitrate. Gives a harder bitrate guarantee, but can cause visible stutter in sustained complex scenes

AV1 encoders have no **Encoding Profile Limit**.

## Further Reading

<xref:Learn-Index-video-encoding-quality-rate-control>
