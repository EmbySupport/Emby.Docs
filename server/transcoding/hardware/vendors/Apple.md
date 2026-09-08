---
uid: Server-Hwa-Vendor-Apple
title: "Apple"
longTitle: "Hardware Acceleration on Apple Hardware"
---

Apple VideoToolbox is the framework macOS exposes for hardware accelerated video encoding and decoding.

## GPU Context Types

**VideoToolbox** is the only context type on macOS.

It differs from every other backend in one respect worth knowing: macOS presents a single, system-wide
media engine rather than individually selectable GPUs. There is therefore exactly one device and at most
one context on the whole machine, no matter what hardware is installed - so nothing here needs choosing
between adapters the way it does on Windows or Linux.

## Drivers

No driver installation is required. VideoToolbox is part of macOS.

## What Your Machine Can Do

Emby detects the encoders, decoders and filters actually offered and shows them in the transcoding
configuration - see [Advanced Mode](../../configuration/Advanced-Mode.md). What is available depends on
the machine's own media engine and the macOS version.

