---
uid: Server-Transcoding-Encoders-VideoToolbox
title: "VideoToolbox"
longTitle: "VideoToolbox Encoder Parameters"
---

On macOS, Emby encodes through [VideoToolbox](xref:Learn-Hardware-Apple-VideoToolbox), the system's video
framework. These parameters apply to the encoders of the VideoToolbox context type - see
[Apple](../../hardware/vendors/Apple.md) for the context type, and [Encoders](Encoders.md) for how the
dialog works. In both encoders, the bitrate Emby requests is passed as the target and maximum rate, with a
buffer of twice the bitrate.

## H.264

The `h264_videotoolbox` encoder for [H.264](xref:Learn-Video-Codec-H264), offered by the VideoToolbox
context type.

**Entropy Coder** - the entropy coding method used to pack the compressed bitstream (ffmpeg `coder`).
Default: **Auto (driver default)**.

- **Auto (driver default)** - sets no method, so VideoToolbox chooses. The recommended starting point
- **CABAC** - better compression than CAVLC, at a higher decoding cost. The usual choice for most content
  and devices
- **CAVLC** - cheaper to decode than CABAC, at a cost in compression efficiency. Mainly useful for very old
  or low-power playback devices that struggle with CABAC

**Prioritize Encoding Speed** - asks VideoToolbox to favour encoding speed over quality (ffmpeg
`prio_speed`). Leave it off to let VideoToolbox decide. Default: off.

**Constant Bit Rate** - requests a truly constant bitrate instead of the usual variation around the target
([CBR](xref:Learn-Video-Encoding-CBR), ffmpeg `constant_bit_rate`). Requires macOS 13 or newer. Default:
off.

**Hardware Encoding** - whether VideoToolbox may use, or must use, its software encoder instead of the
hardware encoder (ffmpeg `allow_sw`, `require_sw`). This is Apple's software encoder inside VideoToolbox,
not one of Emby's [software encoders](Software.md). Default: **Hardware Only**.

- **Hardware Only** - uses hardware encoding only; encoding fails if it is not available
- **Prefer Hardware, Allow Software Fallback** - uses hardware encoding when available, and falls back to
  software encoding instead of failing when it is not
- **Force Software Encoding** - uses software encoding even when hardware encoding is available. Mainly
  useful for troubleshooting hardware-specific problems

**Power-Efficient Encoding** - requests a more power-efficient encoding mode where the hardware offers one
(ffmpeg `power_efficient`). Mainly relevant on battery-powered Macs. Default: off.

**Spatial Adaptive Quantization** - redistributes bits within each frame from complex areas to flat,
low-detail areas, where blocking is most visible (ffmpeg `spatial_aq`). Takes effect only where the
hardware supports it. Default: off.

**Encoding Profile Limit** - the highest H.264 profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Baseline Profile**, **Main Profile** and **High Profile** that VideoToolbox reports.

## HEVC

The `hevc_videotoolbox` encoder for [HEVC](xref:Learn-Video-Codec-HEVC), offered by the VideoToolbox
context type.

**Prioritize Encoding Speed** - asks VideoToolbox to favour encoding speed over quality (ffmpeg
`prio_speed`). Leave it off to let VideoToolbox decide. Default: off.

**Constant Bit Rate** - requests a truly constant bitrate instead of the usual variation around the target
(ffmpeg `constant_bit_rate`). Requires macOS 13 or newer. Default: off.

**Hardware Encoding** - whether VideoToolbox may use, or must use, its software encoder instead of the
hardware encoder (ffmpeg `allow_sw`, `require_sw`). This is Apple's software encoder inside VideoToolbox,
not one of Emby's software encoders. Default: **Hardware Only**.

- **Hardware Only** - uses hardware encoding only; encoding fails if it is not available
- **Prefer Hardware, Allow Software Fallback** - uses hardware encoding when available, and falls back to
  software encoding instead of failing when it is not
- **Force Software Encoding** - uses software encoding even when hardware encoding is available. Mainly
  useful for troubleshooting hardware-specific problems

**Power-Efficient Encoding** - requests a more power-efficient encoding mode where the hardware offers one
(ffmpeg `power_efficient`). Mainly relevant on battery-powered Macs. Default: off.

**Spatial Adaptive Quantization** - redistributes bits within each frame from complex areas to flat,
low-detail areas, where blocking is most visible (ffmpeg `spatial_aq`). Takes effect only where the
hardware supports it. Default: off.

**Encoding Profile Limit** - the highest HEVC profile that may be used; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Main Profile** and **Main 10 Profile** that VideoToolbox reports. Emby does not pass a profile to this
encoder, so the limit only decides whether this device entry is used for a transcode.

## Further Reading

<xref:Learn-Hardware-Apple-Silicon>  
<xref:Learn-Hardware-Encoding>
