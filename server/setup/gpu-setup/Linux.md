---
uid: Server-Gpu-Setup-Linux
title: "GPU Setup on Linux"
legacyUrl: /support/solutions/articles/44001160207-hardware-acceleration-on-linux
redirFromUrl: Hardware-Acceleration-on-Linux.md
---

On Linux, Nvidia hardware needs drivers installed separately, and Rockchip SoCs need a vendor kernel and
device permissions. For Intel and AMD, everything required ships with Emby Server.

What each vendor's hardware can actually do is described under
[Hardware Acceleration](../../transcoding/hardware/Overview.md).

## Nvidia

> [!NOTE]
> Always follow the instructions on the Nvidia site, even when the installed driver version appears to be
> sufficient.

Install the drivers from [Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx) - **not**
from your distribution. The drivers a distribution ships, or offers through its own package manager, often
include [only a subset of what Nvidia provides](xref:Learn-Hardware-Driver-Capabilities), and the missing pieces are frequently exactly the ones
needed for video encoding and decoding.

The minimum required version on Linux is **520.56.06**.

Nvidia works headless - no monitor has to be attached.

## Intel

No setup is required. The [drivers](xref:Learn-Hardware-Linux-VAAPI-Drivers) needed for Intel hardware acceleration are included with Emby Server.

## AMD

No setup is required. The drivers needed for AMD hardware acceleration are included with Emby Server.

## Rockchip

[Rockchip hardware acceleration](xref:Learn-Hardware-Rockchip-MPP) requires the Rockchip BSP (vendor) kernel, 5.10 or 6.1 LTS. All of the
following steps need root permission.

1. Check that `dma_heap`, `dri`, `mpp_service` and `rga` exist in `/dev`:

   ```
   ls -l /dev | grep -E "mpp|rga|dri|dma_heap"
   ```

   If they don't, upgrade the BSP kernel to 5.10 LTS or newer.

2. Grant access to the device files by creating `/etc/udev/rules.d/99-rk-device-permissions.rules` with
   the following content, then restart the machine:

   ```
   KERNEL=="mpp_service", MODE="0660", GROUP="video"
   KERNEL=="rga", MODE="0660", GROUP="video"
   KERNEL=="system", MODE="0666", GROUP="video"
   KERNEL=="system-dma32", MODE="0666", GROUP="video"
   KERNEL=="system-uncached", MODE="0666", GROUP="video"
   KERNEL=="system-uncached-dma32", MODE="0666", GROUP="video" RUN+="/usr/bin/chmod a+rw /dev/dma_heap"
   ```

3. Add the `emby` user to the `render` and `video` groups (on some distributions the group is `input`),
   then restart Emby Server:

   ```
   sudo usermod -aG render emby
   sudo usermod -aG video emby
   sudo systemctl restart emby-server
   ```

4. For [HDR tone mapping](xref:Learn-Tone-Mapping-OpenCL) on the RK3588/RK3588S only: install the Arm Mali [OpenCL runtime](xref:Learn-Hardware-OpenCL) (libmali). Its
   version has to match the kernel driver, otherwise OpenCL does not work:
   - 6.1 LTS kernel on Ubuntu-Rockchip or Armbian, and the legacy 5.10 LTS kernel: **v1.9-1-2131373**
   - 6.1 LTS kernel on other distributions made by board vendors: **v1.9-1-55611b0**

Afterwards, the hardware detection result under **Operations →
[Detection Logs](../../transcoding/operations/Logs.md#detection-logs)** shows whether the SoC was detected.

To watch the hardware at work while a video transcodes, read the VPU and RGA load:

```
sudo sh -c "echo 1000 > /proc/mpp_service/load_interval" && sudo watch -n 1 cat /proc/mpp_service/load
sudo watch -n 1 cat /sys/kernel/debug/rkrga/load
```

VPU load can only be read reliably on BSP kernels from 6.1.84 onwards.

## Further Reading

<xref:Learn-Hardware-Linux-DMABuf>
