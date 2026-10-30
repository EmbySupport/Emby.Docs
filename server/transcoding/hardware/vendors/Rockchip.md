---
uid: Server-Hwa-Vendor-Rockchip
title: "Rockchip"
longTitle: "Hardware Acceleration on Rockchip SoCs"
---

Rockchip SoCs provide hardware accelerated video processing through the
[Rockchip Media Process Platform (RKMPP)](xref:Learn-Hardware-Rockchip-MPP). Two units do the work: the
VPU decodes and encodes video through MPP, and the RGA 2D engine handles scaling, pixel format conversion
and subtitle burn-in. Frames stay in hardware memory all the way from decoding to encoding. The SoC's GPU -
the Mali-G610 on the RK3588 - is only used for HDR tone mapping, through OpenCL.

There is no limit on concurrent encoding sessions, and no monitor needs to be attached.

## GPU Context Types

**Rockchip** is the only context type. Each SoC appears as a single device, named after the chip -
for example *Rockchip RK3588*.

Rockchip hardware acceleration is available when Emby Server runs on Linux.

## How the Work Is Split

A few things work differently from the GPU vendors:

- **Scaling** uses the RGA engine.
- **Deinterlacing** is done by the hardware decoder itself, using the SoC's image enhancement processor
  (IEP).
- **Tone mapping** runs through OpenCL on the SoC's GPU. It is only available on the RK3588 and RK3588S;
  the RGA engines of other SoCs lack the pixel formats it needs.

## Choosing a SoC

The **RK3588/RK3588S** is the recommended choice. Besides the common codecs it decodes 10-bit H.264 and
AV1, and transcodes H.264 and HEVC at up to 1080p at 480 fps or 4K at 120 fps.

- **RK3576** has roughly half the transcoding capacity of the RK3588 and also decodes AV1, but has no
  tone mapping.
- **RK356x** encoders are limited to 1080p at 100 fps, which is not enough for real-time 4K encoding.
- **RK33xx** and older are not recommended - their encoders only handle H.264 at 1080p and 30 fps.

HEVC encoding is available from the RK35xx generation onwards. No current Rockchip SoC encodes AV1.
Check the SoC's datasheet before buying a board for hardware acceleration.

## Hardware Requirements

A Rockchip SoC with an MPP media engine, running a 64-bit Linux distribution with the **Rockchip BSP
(vendor) kernel**, 5.10 or 6.1 LTS. The mainline Linux kernel does not provide the MPP interface.

## Drivers

The kernel drivers are part of the BSP kernel. The user-mode MPP and RGA libraries ship with Emby Server. HDR tone mapping additionally needs the Mali
OpenCL runtime (libmali), and Emby's service user needs access to the device files - see
[GPU Setup on Linux](../../../setup/gpu-setup/Linux.md#rockchip).

## What Your Board Can Do

Emby detects the encoders, decoders and filters the SoC actually offers and shows them in the transcoding
configuration - see [Advanced Mode](../../configuration/Advanced-Mode.md).

## Further Reading

<xref:Learn-Hardware-Linux-DMABuf>  
<xref:Learn-Tone-Mapping-OpenCL>  
[Rockchip MPP](https://github.com/rockchip-linux/mpp), [Rockchip RGA](https://github.com/airockchip/librga)
