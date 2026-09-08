---
uid: Server-Hwa-Vendor-Intel
title: "Intel"
longTitle: "Hardware Acceleration with Intel GPUs"
---

Intel Quick Sync Video is the dedicated media block built into Intel's integrated graphics. It decodes and
encodes without occupying the CPU cores, which is what makes it viable for transcoding on machines whose
processors would otherwise struggle.

## GPU Context Types

An Intel GPU can present several context types at once, and Emby prefers Quick Sync where it is available.

**QsvWindows** is Quick Sync on Windows, using D3D11VA interop - or on older systems and drivers, the
legacy DXVA2 interop.

**QsvLinux** is the same Quick Sync media block on Linux, reached through VAAPI interop. The underlying
filters are the same ones Windows uses; only the surrounding interop differs.

**VulkanIntel** is the generic, cross-vendor Vulkan interface on the same card. It is a separate context
available alongside Quick Sync, not a replacement for it.

**Vaapi** is the generic, vendor-agnostic VAAPI context. It appears when the card's VAAPI encoder did not
identify itself as Quick Sync specifically, which is why it can show up alongside the QSV contexts rather
than instead of them.

Which of these exist on your machine, and which one is in use, is shown per device in
[Advanced Mode](../../configuration/Advanced-Mode.md).

## Hardware Requirements

<!-- REVIEW: hardware generation claim carried over from the previous article, not verified -->
Quick Sync first appeared in some Sandy Bridge CPUs, though not in the Sandy Bridge Pentium or Celeron
parts. Which codecs a given generation can handle is documented in Intel's own material and summarised in
[Hardware decoding and encoding](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding)
and [GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration)).

## Drivers

On Linux nothing needs installing - the necessary drivers ship with Emby Server. On Windows, install
Intel's graphics drivers. See [GPU Setup](../../../setup/gpu-setup/GPU-Setup.md).

## What Your Card Can Do

Emby detects the encoders, decoders and filters each device actually offers, rather than assuming them
from the model name, and shows them per device in the transcoding configuration. What a given GPU
supports depends on its generation, its driver and the operating system, so the configuration is the
authoritative answer for your own hardware.

## Further Reading

[Intel Quick Sync Video](https://www.intel.com/content/www/us/en/architecture-and-technology/quick-sync-video/quick-sync-video-general.html)  
[Video Acceleration API](https://en.wikipedia.org/wiki/Video_Acceleration_API)  
[VAAPI supported hardware and drivers](https://en.wikipedia.org/wiki/Video_Acceleration_API#Supported_hardware_and_drivers)  
[Codec Support by CPU Generation](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding)  
[GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration))
