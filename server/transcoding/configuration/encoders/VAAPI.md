---
uid: Server-Transcoding-Encoders-Vaapi
title: "VAAPI"
longTitle: "VAAPI Encoder Parameters"
---

[VAAPI](xref:Learn-Hardware-Linux-VAAPI) is the video acceleration interface of Linux. These parameters
apply to the VAAPI encoders of the VAAPI (Intel) and VAAPI (AMD) context types - see
[Intel](../../hardware/vendors/Intel.md) and [AMD](../../hardware/vendors/AMD.md) for the context types,
and [Encoders](Encoders.md) for how the dialog works. How closely a setting is followed depends on the
GPU's VAAPI driver.

## H.264

The `h264_vaapi` encoder for [H.264](xref:Learn-Video-Codec-H264), offered by the VAAPI (Intel) and VAAPI
(AMD) context types.

**Compression Level** - trades encoding speed against quality as a small number, where higher values are
faster and give lower quality (ffmpeg `compression_level`). Range 1 to 7; the highest usable value depends
on the device. Leave it empty (the default) for the driver's default.

**Bitrate Mode** - how the bitrate Emby requests is passed to the encoder. Default: **Classic
(CBR-like)**.

- **Classic (CBR-like)** - sets the target bitrate, a maximum rate equal to it and a buffer of twice the
  bitrate ([VBV](xref:Learn-Video-Encoding-VBV)), and leaves the rate control mode to the encoder: a
  constrained, CBR-like behaviour
- **Variable Bitrate (VBR)** - selects VBR rate control (ffmpeg `rc_mode` `VBR`) with the requested
  bitrate as the target, letting the bitrate vary with scene complexity
  ([VBR](xref:Learn-Video-Encoding-VBR)). Generally better quality for the same amount of data than
  Classic, with a less predictable size
- **Constant Bitrate (CBR)** - selects CBR rate control (ffmpeg `rc_mode` `CBR`) with the requested
  bitrate as both target and maximum rate ([CBR](xref:Learn-Video-Encoding-CBR)). For strict bandwidth
  limits

**Entropy Coder** - the entropy coding method used to pack the compressed bitstream (ffmpeg `coder`).
Default: **CABAC**.

- **CABAC** - better compression than CAVLC, at a higher decoding cost. The recommended choice for most
  content and devices
- **CAVLC** - cheaper to decode than CABAC, at a cost in compression efficiency. Mainly useful for very old
  or low-power playback devices that struggle with CABAC

**Encoding Profile Limit** - the highest H.264 profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Constrained Baseline Profile**, **Main Profile** and **High Profile** that the driver reports.

## HEVC

The `hevc_vaapi` encoder for [HEVC](xref:Learn-Video-Codec-HEVC), offered by the VAAPI (Intel) and VAAPI
(AMD) context types.

**Bitrate Mode** - how the bitrate Emby requests is passed to the encoder. Default: **Classic
(CBR-like)**.

- **Classic (CBR-like)** - sets the target bitrate, a maximum rate equal to it and a buffer of twice the
  bitrate, and leaves the rate control mode to the encoder: a constrained, CBR-like behaviour
- **Variable Bitrate (VBR)** - selects VBR rate control (ffmpeg `rc_mode` `VBR`) with the requested
  bitrate as the target, letting the bitrate vary with scene complexity. Generally better quality for the
  same amount of data than Classic, with a less predictable size
- **Constant Bitrate (CBR)** - selects CBR rate control (ffmpeg `rc_mode` `CBR`) with the requested
  bitrate as both target and maximum rate. For strict bandwidth limits

**Tier** - the HEVC [tier](xref:Learn-Video-Codec-Levels-Tiers), which sets the maximum bitrate allowed at
the encoding level in use (ffmpeg `tier`). Default: **Main**.

- **Main** - the standard tier, sufficient for the vast majority of content and bitrates
- **High** - allows a higher maximum bitrate at a given level. Only relevant for unusually high bitrates;
  most playback devices support the Main tier only

**Include HDR Metadata** - has the encoder write the
[mastering display](xref:Learn-HDR-Mastering-Display-Metadata) and
[content light level](xref:Learn-HDR-MaxCLL-MaxFALL) metadata of an HDR source into the output, which
players need to display HDR content correctly (ffmpeg `sei` `hdr`). Only meaningful when the source is
HDR. When off, the encoder's own default applies. Default: off.

**Encoding Profile Limit** - the highest HEVC profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Main Profile**, **Main 10 Profile** and **Range Extension (REXT)** that the driver reports.

## AV1

The `av1_vaapi` encoder for [AV1](xref:Learn-Video-Codec-AV1), offered by the VAAPI (Intel) and VAAPI
(AMD) context types.

**Bitrate Mode** - how the bitrate Emby requests is passed to the encoder. Default: **Classic
(CBR-like)**.

- **Classic (CBR-like)** - sets the target bitrate, a maximum rate equal to it and a buffer of twice the
  bitrate, and leaves the rate control mode to the encoder: a constrained, CBR-like behaviour
- **Variable Bitrate (VBR)** - selects VBR rate control (ffmpeg `rc_mode` `VBR`) with the requested
  bitrate as the target, letting the bitrate vary with scene complexity. Generally better quality for the
  same amount of data than Classic, with a less predictable size
- **Constant Bitrate (CBR)** - selects CBR rate control (ffmpeg `rc_mode` `CBR`) with the requested
  bitrate as both target and maximum rate. For strict bandwidth limits

**Tier** - the AV1 tier, which sets the maximum bitrate allowed at the encoding level in use (ffmpeg
`tier`). Default: **Main**.

- **Main** - the standard tier, sufficient for the vast majority of content and bitrates
- **High** - allows a higher maximum bitrate at a given level. Only relevant for unusually high bitrates;
  most playback devices support the Main tier only

**Enable Low-Power Encoding** - uses the GPU's [fixed-function](xref:Learn-Hardware-Fixed-Function)
encoding mode (ffmpeg `low_power`). It is often faster, but lower in quality. Transcoding fails if the
hardware does not support this mode for the codec. Default: off.

AV1 encoders have no **Encoding Profile Limit**.

## Further Reading

<xref:Learn-Hardware-Linux-VAAPI-Drivers>  
<xref:Learn-Index-video-encoding-quality-rate-control>
