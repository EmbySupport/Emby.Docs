---
uid: Server-Hwa-Vendor-Amd
title: "AMD"
longTitle: "Hardware Acceleration with AMD GPUs"
---

[AMD Advanced Media Framework (AMF)](xref:Learn-Hardware-AMD-AMF) is AMD's multimedia framework for real-time video processing. It
abstracts the platform and API details underneath it, and gives Emby access to the [video engines](xref:Learn-Hardware-AMD-VCN) built
into Radeon GPUs and APUs.

## GPU Context Types

An AMD GPU can present several context types at once, and Emby prefers AMF where it is available.
Which ones exist depends on the operating system.

**Windows**

- **AMF on D3D11** - AMF, using D3D11 interop
- **AMF on Vulkan** - AMF, using Vulkan interop
- **Vulkan (AMD)** - **experimental** - the generic, cross-vendor [Vulkan interface](xref:Learn-Hardware-Vulkan) on the same card

**Linux**

- **AMF on Vulkan** - AMF, using Vulkan interop
- **VAAPI (AMD)** - [VAAPI](xref:Learn-Hardware-Linux-VAAPI) on its own; currently disabled
- **Vulkan (AMD)** - **experimental**

The Vulkan context is a separate context available alongside AMF, not a replacement for it.

Which of these exist on your machine, and which one is in use, is shown per device in
[Advanced Mode](../../configuration/Advanced-Mode.md).

## Hardware Requirements

Which codecs each generation of AMD's video engines can handle is described in
[AMD VCN generation capabilities](xref:Learn-Hardware-AMD-VCN-Generations).

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
