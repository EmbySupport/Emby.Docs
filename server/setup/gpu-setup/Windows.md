---
uid: Server-Gpu-Setup-Windows
title: "GPU Setup on Windows"
legacyUrl: /support/solutions/articles/44001160185-hardware-acceleration-on-windows
redirFromUrl: Hardware-Acceleration-on-Windows.md
---

On Windows, each vendor needs its own graphics drivers installed. In every case, install the drivers from
the manufacturer rather than relying on the ones Windows supplies - the in-box drivers frequently lack the
[media components](xref:Learn-Hardware-Driver-Capabilities) Emby needs. None of the vendors require their SDK to be installed.

What each vendor's hardware can actually do is described under
[Hardware Acceleration](../../transcoding/hardware/Overview.md).

## Nvidia

Install the current drivers from [Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx).
The minimum required version on Windows is **522.25**. The Nvidia SDKs are not needed.

Nvidia works headless - no monitor has to be attached - and works when Emby runs as a Windows service.

## Intel

Install the current Intel graphics drivers from [Intel](https://www.intel.com/content/www/us/en/download-center/home.html).
The [Intel Media SDK](xref:Learn-Hardware-Intel-Media-SDK) is not needed.

## AMD

Install the current Radeon software from [AMD Drivers & Support](https://www.amd.com/en/support). The [AMF](xref:Learn-Hardware-AMD-AMF)
SDK is not needed.

A recent driver version is required.

## Running Emby as a Service

For running Emby as a Windows service, see [Running as Windows Service](../../../Run-as-Windows-Service.md).

## Remote Desktop

Hardware acceleration can stop working while connected over RDP. See
[Hardware Acceleration fails with RDP](../../transcoding/Hwa-Fails-with-RDP.md).

## Further Reading

<xref:Learn-Index-hardware-acceleration-interfaces-windows>
