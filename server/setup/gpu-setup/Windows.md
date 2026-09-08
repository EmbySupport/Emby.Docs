---
uid: Server-Gpu-Setup-Windows
title: "GPU Setup on Windows"
legacyUrl: /support/solutions/articles/44001160185-hardware-acceleration-on-windows
redirFromUrl: Hardware-Acceleration-on-Windows.md
---

On Windows, each vendor needs its own graphics drivers installed. In every case, install the drivers from
the manufacturer rather than relying on the ones Windows supplies - the in-box drivers frequently lack the
media components Emby needs. None of the vendors require their SDK to be installed.

What each vendor's hardware can actually do is described under
[Hardware Acceleration](../../transcoding/hardware/Overview.md).

## Nvidia

Install the current drivers from [Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx).
<!-- REVIEW: minimum driver version carried over from the previous article, not verified -->
The minimum required version on Windows is **471.41**. The Nvidia SDKs are not needed.

<!-- REVIEW: headless / service behaviour carried over from the previous article, not verified -->
Nvidia works headless - no monitor has to be attached - and works when Emby runs as a Windows service.

## Intel

Install the current Intel graphics drivers from [Intel](https://www.intel.com/content/www/us/en/download-center/home.html).
The Intel Media SDK is not needed.

<!-- REVIEW: headless / service behaviour carried over from the previous article, not verified -->
Headless operation, and running as a Windows service, work when the D3D11 codec is in use. Otherwise a
physical monitor has to be connected to the video output.

## AMD

Install the current Radeon software from [AMD Drivers & Support](https://www.amd.com/en/support). The AMF
SDK is not needed.

<!-- REVIEW: minimum driver version carried over from the previous article, not verified -->
The minimum required version is **AMD Radeon Software Crimson Edition 16.7.3 (16.30.2311)**.

<!-- REVIEW: headless / service behaviour carried over from the previous article, not verified -->
AMD does not currently support headless operation - a physical monitor has to be connected to the video
output - and AMF acceleration does not work when Emby runs as a Windows service.

## Running Emby as a Service

Whether hardware acceleration survives running as a service depends on the vendor, as noted above. For the
service itself, see [Running as Windows Service](../../../Run-as-Windows-Service.md).

## Remote Desktop

Hardware acceleration can stop working while connected over RDP. See
[Hardware Acceleration fails with RDP](../../transcoding/Hwa-Fails-with-RDP.md).
