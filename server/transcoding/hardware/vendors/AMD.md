---
uid: Server-Hwa-Vendor-Amd
title: "AMD"
longTitle: "Hardware Acceleration with AMD GPUs"
---

AMD Advanced Media Framework (AMF) is AMD's multimedia framework for real-time video processing. It
abstracts the platform and API details underneath it, and gives Emby access to the video engines built
into Radeon GPUs and APUs.

## GPU Context Types

An AMD GPU can present several context types at once, and Emby prefers AMF where it is available.

**AmdWindows** is AMF on Windows.

**AmdLinux** is AMF on Linux.

**VulkanAmd** is the generic, cross-vendor Vulkan interface on the same card - a separate context
available alongside AMF, not a replacement for it.

**Vaapi** is the generic, vendor-agnostic VAAPI context. It appears when the card's VAAPI encoder did not
identify itself as AMF specifically, which is why it can show up alongside the AMF contexts rather than
instead of them.

Which of these exist on your machine, and which one is in use, is shown per device in
[Advanced Mode](../../configuration/Advanced-Mode.md).

## Hardware Requirements

<!-- REVIEW: hardware generation claim carried over from the previous article, not verified -->
AMF works with most recent Radeon GPUs from the Southern Islands family onwards, and with APUs of the
Kabini, Kaveri and Carrizo families and newer.

## Drivers

On Linux nothing needs installing - the necessary drivers ship with Emby Server. On Windows, install the
Radeon software. See [GPU Setup](../../../setup/gpu-setup/GPU-Setup.md).

## What Your Card Can Do

Emby detects the encoders, decoders and filters each device actually offers, rather than assuming them
from the model name, and shows them per device in the transcoding configuration. What a given GPU
supports depends on its generation, its driver and the operating system, so the configuration is the
authoritative answer for your own hardware.

## Further Reading

[AMD Advanced Media Framework](https://gpuopen.com/gaming-product/advanced-media-framework/)  
[Video Acceleration API](https://en.wikipedia.org/wiki/Video_Acceleration_API)  
[VAAPI supported hardware and drivers](https://en.wikipedia.org/wiki/Video_Acceleration_API#Supported_hardware_and_drivers)  
[AMF SDK](https://github.com/GPUOpen-LibrariesAndSDKs/AMF)  
[AMD Drivers & Support](https://www.amd.com/en/support)
