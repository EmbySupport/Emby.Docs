---
uid: Server-Transcoding-Encoders-Rockchip
title: "Rockchip"
longTitle: "Rockchip Encoder Parameters"
---

Rockchip SoCs encode through the [Rockchip Media Process Platform (RKMPP)](xref:Learn-Hardware-Rockchip-MPP).
These parameters apply to the encoders of the Rockchip context type - see
[Rockchip](../../hardware/vendors/Rockchip.md) for the context type and which SoCs encode HEVC, and
[Encoders](Encoders.md) for how the dialog works. In both encoders, the bitrate Emby requests is passed as
the target and maximum rate, with a buffer of twice the bitrate; the rate control method decides how the
encoder uses them.

## H.264

The `h264_rkmpp` encoder for [H.264](xref:Learn-Video-Codec-H264), offered by the Rockchip context type.

**Rate Control Method** - how the encoder reaches the bitrate Emby requests (ffmpeg `rc_mode`). Default:
**Auto (driver default)**.

- **Auto (driver default)** - sets no method, so the encoder uses its own default. The recommended
  starting point
- **Constant Bitrate (CBR)** - holds the bitrate as close to constant as possible, regardless of scene
  complexity ([CBR](xref:Learn-Video-Encoding-CBR)). Useful for strict bandwidth limits, at the cost of
  quality consistency across scenes
- **Variable Bitrate (VBR)** - targets an average bitrate and lets it vary with scene complexity
  ([VBR](xref:Learn-Video-Encoding-VBR)). Generally better quality for the same amount of data, with a less
  predictable size
- **Adaptive VBR (AVBR)** - variable bitrate that drops well below the target for static or simple scenes
  and rises up to it for complex ones, saving data where the picture allows it
- **Constant QP** - encodes every frame with the same fixed
  [quantization parameter](xref:Learn-Video-Encoding-QP), set by **Constant QP Value**: predictable
  per-frame quality, unpredictable size. Rarely the right choice for streaming

**Constant QP Value** - the quantization parameter used for every frame with the **Constant QP** method
(ffmpeg `qp_init`). Lower values give higher quality and larger output. Range 0 to 51, default **26**,
which is also used when the field is empty. Shown only when **Rate Control Method** is **Constant QP**.

**Entropy Coder** - the entropy coding method used to pack the compressed bitstream (ffmpeg `coder`).
Default: **Auto (driver default)**.

- **Auto (driver default)** - sets no method, so the encoder chooses. The recommended starting point
- **CABAC** - better compression than CAVLC, at a higher decoding cost. The usual choice for most content
  and devices
- **CAVLC** - cheaper to decode than CABAC, at a cost in compression efficiency. Mainly useful for very old
  or low-power playback devices that struggle with CABAC

**Encoding Profile Limit** - the highest H.264 profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers those of
**Baseline Profile**, **Main Profile** and **High Profile** that the SoC reports.

## HEVC

The `hevc_rkmpp` encoder for [HEVC](xref:Learn-Video-Codec-HEVC), offered by the Rockchip context type.

**Rate Control Method** - how the encoder reaches the bitrate Emby requests (ffmpeg `rc_mode`). Default:
**Auto (driver default)**.

- **Auto (driver default)** - sets no method, so the encoder uses its own default. The recommended
  starting point
- **Constant Bitrate (CBR)** - holds the bitrate as close to constant as possible, regardless of scene
  complexity. Useful for strict bandwidth limits, at the cost of quality consistency across scenes
- **Variable Bitrate (VBR)** - targets an average bitrate and lets it vary with scene complexity.
  Generally better quality for the same amount of data, with a less predictable size
- **Adaptive VBR (AVBR)** - variable bitrate that drops well below the target for static or simple scenes
  and rises up to it for complex ones, saving data where the picture allows it
- **Constant QP** - encodes every frame with the same fixed quantization parameter, set by **Constant QP
  Value**: predictable per-frame quality, unpredictable size. Rarely the right choice for streaming

**Constant QP Value** - the quantization parameter used for every frame with the **Constant QP** method
(ffmpeg `qp_init`). Lower values give higher quality and larger output. Range 0 to 51, default **26**,
which is also used when the field is empty. Shown only when **Rate Control Method** is **Constant QP**.

**Tier** - the HEVC [tier](xref:Learn-Video-Codec-Levels-Tiers), which sets the maximum bitrate allowed at
the encoding level in use (ffmpeg `tier`). Emby always passes the tier, because the encoder would otherwise
use the High tier. Default: **Main**.

- **Main** - the standard tier, sufficient for the vast majority of content and bitrates
- **High** - allows a higher maximum bitrate at a given level. Only relevant for unusually high bitrates;
  most playback devices support the Main tier only

**Encoding Profile Limit** - the highest HEVC profile the encoder may use; empty (the default) means no
limit - see [Encoding Profile Limit](Encoders.md#encoding-profile-limit). Offers **Main Profile** where the
SoC reports it.

## Further Reading

<xref:Learn-Index-video-encoding-quality-rate-control>
