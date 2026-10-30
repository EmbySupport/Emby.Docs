---
uid: Server-Hwa-Vendor-Intel
title: "Intel"
longTitle: "Hardware Acceleration with Intel GPUs"
---

[Intel Quick Sync Video](xref:Learn-Hardware-Intel-QSV) is the dedicated media block built into Intel's integrated graphics. It decodes and
encodes without occupying the CPU cores, which is what makes it viable for transcoding on machines whose
processors would otherwise struggle.

## GPU Context Types

An Intel GPU can present several context types at once, and Emby prefers Quick Sync where it is available.
Which ones exist depends on the operating system.

**Windows**

- **QSV on D3D11** - Quick Sync, using [D3D11VA](xref:Learn-Hardware-Windows-D3D11VA) interop
- **Vulkan (Intel)** - **experimental** - the generic, cross-vendor [Vulkan interface](xref:Learn-Hardware-Vulkan) on the same card

**Linux**

- **QSV on VAAPI** - the same Quick Sync media block, reached through [VAAPI](xref:Learn-Hardware-Linux-VAAPI) interop. The
  [underlying filters](xref:Learn-Hardware-Intel-VPP) are the same ones Windows uses; only the surrounding interop differs
- **VAAPI (Intel)** - VAAPI on its own, without Quick Sync
- **Vulkan (Intel)** - **experimental**

The Vulkan context is a separate context available alongside Quick Sync, not a replacement for it.

Which of these exist on your machine, and which one is in use, is shown per device in
[Advanced Mode](../../configuration/Advanced-Mode.md).

## Hardware Requirements

Which codecs [a given generation](xref:Learn-Index-hardware-acceleration-generations-intel) can handle is documented in Intel's own material and summarised in
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
