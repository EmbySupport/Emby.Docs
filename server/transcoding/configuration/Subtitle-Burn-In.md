---
uid: Server-Transcoding-Subtitle-Burn-In
title: "Subtitle Burn-In"
longTitle: "Subtitle Burn-In per Device"
---

When an app cannot display the subtitles that were selected, they have to be
[burned into the video](xref:Learn-Subtitle-Burn-In): they become part of the picture, which always
requires transcoding - see [Why Is My Media Transcoding?](../Why-Media-Transcodes.md#are-subtitles-selected).
How that is done is configured per device, in the **Subtitles** section of the device's configuration dialog
- see [Device Configuration](Advanced-Mode.md#device-configuration) and
[GPU Config](Expert-Node-Types.md#gpu-config).

The section has two selections:

- **Text subtitles** - for [text-based subtitles](xref:Learn-Subtitle-Text) such as SRT and ASS, including
  [closed captions](xref:Learn-Caption-CTA-608)
- **Graphic subtitles** - for [subtitle images](xref:Learn-Subtitle-Bitmap) such as PGS, VobSub and DVB

A selection is only shown when the device's context type offers at least one way of burning in that kind
of subtitles.

## Choices

The choices differ in where the subtitles are combined with the video - on the CPU or on the GPU - and in
whose subtitle processing does it: FFmpeg's own, or Emby's. They are listed in the order the dropdowns show
them; which of them a context type offers is listed [below](#choices-per-context-type).

**Burn in on GPU, bitmaps only (Emby)** - the subtitles are rendered on the CPU, and only the images of the
subtitle areas are uploaded to the GPU, which combines them with the video. The video stays on the GPU
throughout, and the least data is transferred.

**Burn in on GPU, full frames (Emby)** - the subtitles are rendered on the CPU into full-size transparent
frames, which are uploaded to the GPU and combined with the video there. The video stays on the GPU, but a
full frame is uploaded for each subtitle frame.

**Burn in on GPU, full frames (FFmpeg)** - *Graphic subtitles only.* As above, using FFmpeg's own subtitle
handling, which scales the whole subtitle canvas to the video.

**Burn in on CPU (Emby)** - the subtitles are burned in on the CPU, using Emby's subtitle processing. When
the video was decoded on the GPU, each frame is copied to the CPU for this and uploaded again for encoding.
For text subtitles this choice also handles closed captions and ARIB captions; for graphic subtitles it fits
the subtitles into the picture.

**Burn in on CPU (FFmpeg)** - the subtitles are burned in on the CPU, using FFmpeg's own subtitle filters,
with the same copying between GPU and CPU. It cannot burn in closed captions or ARIB captions, and for
graphic subtitles it scales the whole subtitle canvas to the video.

**Skip this configuration** - the device entry is not used for operations that have to burn in this kind of
subtitles. Evaluation moves on to the next entry in the graph - see
[Graph Evaluation](Expert-Graph-Evaluation.md).

## Choices per Context Type

| Context types | Text subtitles | Graphic subtitles |
|---|---|---|
| Nvidia CUDA, QSV on D3D11, QSV on VAAPI, VAAPI (Intel), AMF on Vulkan, Vulkan (Nvidia), Vulkan (Intel), Vulkan (AMD), Rockchip | all choices | all choices |
| AMF on D3D11 | GPU bitmaps only, and both CPU choices | GPU bitmaps only, and both CPU choices |
| VideoToolbox, Software | both CPU choices | both CPU choices |
| MediaCodec | both CPU choices | not offered |

The default is the first choice a context type offers: **Burn in on GPU, bitmaps only (Emby)** where it is
available, otherwise **Burn in on CPU (Emby)**. With MediaCodec, a device entry is never used when graphic
subtitles have to be burned in.

## Avoiding Burn-In

Burning in subtitles is always more work than delivering them to the app separately. Graphic subtitles can
often be avoided by converting them to text with [OCR Conversion](../subtitles/OCR-Conversion.md); for text
subtitles embedded in the video, see
[On-the-Fly Subtitle Extraction](../Settings.md#on-the-fly-subtitle-extraction).

## Further Reading

<xref:Learn-Subtitle-Pipeline-Fundamentals>  
<xref:Learn-Subtitle-Pipeline-Hardware>  
<xref:Learn-Hardware-Copy-Back>
