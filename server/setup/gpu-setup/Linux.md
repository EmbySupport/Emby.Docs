---
uid: Server-Gpu-Setup-Linux
title: "GPU Setup on Linux"
legacyUrl: /support/solutions/articles/44001160207-hardware-acceleration-on-linux
redirFromUrl: Hardware-Acceleration-on-Linux.md
---

On Linux, only Nvidia hardware needs drivers installed separately. For Intel and AMD, everything required
ships with Emby Server.

What each vendor's hardware can actually do is described under
[Hardware Acceleration](../../transcoding/hardware/Overview.md).

## Nvidia

> [!NOTE]
> Always follow the instructions on the Nvidia site, even when the installed driver version appears to be
> sufficient.

Install the drivers from [Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx) - **not**
from your distribution. The drivers a distribution ships, or offers through its own package manager, often
include only a subset of what Nvidia provides, and the missing pieces are frequently exactly the ones
needed for video encoding and decoding.

<!-- REVIEW: minimum driver version carried over from the previous article, not verified -->
The minimum required version on Linux is **470.57**.

Nvidia works headless - no monitor has to be attached.

## Intel

No setup is required. The drivers needed for Intel hardware acceleration are included with Emby Server.

## AMD

No setup is required. The drivers needed for AMD hardware acceleration are included with Emby Server.

## Containers

Running Emby in a container adds device passthrough on top of the above - see
[Containers](Containers.md).
