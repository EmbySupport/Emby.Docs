---
uid: Server-Hwa-Vendor-Nvidia
title: "Nvidia"
longTitle: "Hardware Acceleration with Nvidia GPUs"
---

Nvidia GPUs carry dedicated video engines that are separate from the CUDA cores: NVENC for encoding and
NVDEC (formerly NVCUVID) for decoding. Because the work runs on those engines rather than on the graphics
engine or the CPU, both stay free for other things, and the engines are fast enough to transcode
considerably faster than real time.

## GPU Context Types

Emby offers up to two context types for an Nvidia card, and most cards present both at the same time.

**NvEnc** is Nvidia's own interface, and the one Emby picks by default. The interop is identical on
Windows and Linux, so nothing about this context differs between the two.

**VulkanNvidia** is the generic, cross-vendor Vulkan interface running on the same card. It is a separate
context that sits alongside NvEnc rather than replacing it, and it is generally the less mature of the
two. It is worth trying when a specific operation fails under NvEnc, or when you want to compare.

Which one is in use, and which are available at all, is shown per device in
[Advanced Mode](../../configuration/Advanced-Mode.md). Expert Mode additionally lets the same card appear
more than once with a different context each time - see
[Expert Mode](../../configuration/Expert-Mode.md).

## Nvidia-Specific Options

The NvEnc context carries a few behaviour options of its own, reachable from the device's configuration
dialog:

- What should happen when no suitable hardware decoder is available for a given media type - fall back to
  software decoding, or skip this configuration entirely
- Whether to use decoder-side (CUVID) deinterlacing
- Whether to use decoder-side (CUVID) scaling

## Hardware Requirements

<!-- REVIEW: hardware generation claim carried over from the previous article, not verified -->
Hardware acceleration is available on most Nvidia devices from the Kepler generation onwards (e.g. GeForce
GT 630), both consumer and professional. Nvidia's own
[GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix) lists which
codecs each chip generation can encode and decode.

## Drivers

Nvidia cards need drivers installed on the server, and on Linux specifically they need Nvidia's own
drivers rather than the ones a distribution ships. See [GPU Setup](../../../setup/gpu-setup/GPU-Setup.md).

## What Your Card Can Do

Emby detects the encoders, decoders and filters each device actually offers, rather than assuming them
from the model name, and shows them per device in the transcoding configuration. What a given card
supports depends on its generation, its driver and the operating system, so the configuration is the
authoritative answer for your own hardware.

## Further Reading

[Nvidia Video Codec SDK](https://developer.nvidia.com/nvidia-video-codec-sdk)  
[GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix)  
[NVENC](https://en.wikipedia.org/wiki/Nvidia_NVENC), [NVDEC](https://en.wikipedia.org/wiki/Nvidia_NVDEC)
