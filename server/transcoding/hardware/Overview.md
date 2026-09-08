---
uid: Hardware-Acceleration-Overview
title: Hardware Acceleration Overview
legacyUrl: /support/solutions/articles/44001160148-hardware-acceleration-overview
redirFromUrl: Hardware-Acceleration-Overview.md
---

Transcoding in software is demanding work for a CPU. Most modern GPUs and SoCs carry dedicated video
engines that decode and encode far more cheaply, and Emby can hand the work to them instead. That is
hardware acceleration: the same transcode, performed by silicon built for it, leaving the CPU free.

## Devices and Context Types

A physical GPU is one **device**. Each device offers one or more **context types** - a particular
hardware-acceleration interface for reaching that device's video engines.

A device commonly offers more than one at the same time. An Nvidia card typically presents both NvEnc and
Vulkan; an Intel card can present Quick Sync, Vulkan and VAAPI simultaneously. These are alternative ways
of using the same silicon, and they differ in maturity, in which filters they support, and sometimes in
which operations succeed at all. Emby chooses a sensible default per device - the vendor's own interface
where one exists - and the configuration lets you choose differently.

## Vendors

- [Nvidia](vendors/Nvidia.md) - NVENC/NVDEC and Vulkan
- [Intel](vendors/Intel.md) - Quick Sync, Vulkan and VAAPI
- [AMD](vendors/AMD.md) - AMF, Vulkan and VAAPI
- [Apple](vendors/Apple.md) - VideoToolbox
- [Android](vendors/Android.md) - MediaCodec
- [Rockchip](vendors/Rockchip.md) - RKMPP, prepared but not yet active

## What Your Hardware Can Do

Emby does not infer capabilities from a model name. It detects the encoders, decoders and filters each
device actually offers, per context type, and reports them in the transcoding configuration. Because what
a device can do depends on its generation, its drivers and the operating system, that configuration is
the authoritative answer for your own machine - more so than any table in documentation could be.

## Getting Started

Drivers and any other server-side preparation are covered under
[GPU Setup](../../setup/gpu-setup/GPU-Setup.md). Once the hardware is visible to Emby, how it gets used
is decided in the [transcoding configuration](../configuration/Transcoding-Configuration.md).

If something is not working as expected, see [Troubleshooting](../Troubleshooting.md).
