Emby supports the following hardware acceleration variants on Windows

- **[Nvidia NVDEC & NVENC](#nvidia-nvdec-nvenc)**  
API for video encoding and decoding acceleration using Nvidia GPUs

- **[Intel QuickSync Video](#intel-quicksync-video)**  
 Intel's brand for its dedicated video encoding and decoding hardware 
 core

- **[AMD AMF](#AMD-AMF)**  
 AMD Advanced Media Framework - multimedia API  AMD hardware for 
 real-time processing of multimedia

- **[Microsoft DXVA](#Microsoft-DXVA)**  
 Microsoft DirectX Video Acceleration API - hardware independent API 
 for hardware accelerated video decoding

## Nvidia NVDEC & NVENC
Nvidia provides two hardware acceleration interfaces: 
- NVENCODE API for video encode acceleration
- NVDECODE API for video decode acceleration (formerly called NVCUVID API)

NVIDIA GPUs contain one or more hardware-based decoder and encoder(s) (separate from the CUDA cores) which provides fully-accelerated hardware-based video decoding and encoding for several popular codecs. With decoding/encoding offloaded, the graphics engine and the CPU are free for other operations. 

GPU hardware accelerator engines for video decoding (referred to as NVDEC) and video encoding (referred to as NVENC) support faster than real-time video processing which makes them suitable to be used for transcoding applications, in addition to video playback. 

#### Supported Accelerations
The following accelerations are currently supported by Emby.
Please note that Emby may not support all accelerations offered by the hardware 
and that not all hardware devices will support all accelerations.

- Decoders
  - H.264 (AVC)
  - H.265 (HEVC)
  - MPEG2
  - MPEG4
  - VC1
  - VP8
  - VP9
- Encoders
  - H.264 (AVC)

#### Hardware Requirements
Hardware acceleration is available for most Nvidia devices starting with GPUs from the 
Kepler generation (e.g. GeForce GT 630) onwards, including both consumer and professional
devices. Detailed information about supported hardware can be found in Nvidias 
[GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix).

#### Required Setup Steps

Install the latest drivers for your Nvidia hardware directly from 
[Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx) page.
It is highly recommended to use these drivers instead of the ones that are 
shipped with Windows.
The minimum required driver version on Windows is **390.77**  
It is not required to install any other tools or SDKs from Nvidia.

#### Remarks

- Emby supports headless operation for Nvidia  
  It is not required to connect a monitor
- Nvidia acceleration also works when Emby is run as a Windows service

#### Further Reading
[Nvidia Video Codec SDK](https://developer.nvidia.com/nvidia-video-codec-sdk)  
[GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix)  
[Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx)  
[NVENC](https://en.wikipedia.org/wiki/Nvidia_NVENC), 
[NVDEC](https://en.wikipedia.org/wiki/Nvidia_NVDEC)

## Intel QuickSync Video
Intel® Quick Sync Video uses the dedicated media processing capabilities of Intel® Graphics Technology to decode and encode fast, enabling the processor to complete other tasks and improving system responsiveness.

#### Supported Accelerations
The following accelerations are currently supported by Emby.
Please note that Emby may not support all accelerations offered by the hardware 
and that not all hardware devices will support all accelerations.

- Decoders
  - H.264 (AVC)
  - H.265 (HEVC)
  - MPEG2
  - VC1
  - VP8
  - VP9
- Encoders
  - H.264 (AVC)
- Hardware Filters
  - Scaling
  - Deinterlacing

#### Hardware Requirements
Quick Sync was initially built into some Sandy Bridge CPUs, but not into Sandy Bridge Pentiums or Celerons.  
An overview of acceleration capabilities built into the various CPU generations
can be found here: [Hardware decoding and encoding](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding).
and here [GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration)).

#### Required Setup Steps

Install the latest graphics drivers for your Intel COU with integrated graphics
directly from Intel's site: [Drivers & Software](https://downloadcenter.intel.com/) 
It is highly recommended to use these drivers instead of the ones that are 
shipped with Windows.
It is not required to install the Intel Media SDK.

#### Remarks

- Emby currently **does not support** headless operation with Intel QuickSync
  You will either need to connect a physical monitor to the video output
  or you can acquire a "dummy monitor plug" to make the GPU think that 
  a monitor is connected
- QuickSync acceleration **does not work** when Emby is run as a Windows service

``Note: Support for headless mode is planned for the future``

#### Further Reading
[Intel QuickSync Video](https://www.intel.com/content/www/us/en/architecture-and-technology/quick-sync-video/quick-sync-video-general.html)  
[Codec Support by CPU Generation](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding)  
[GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration))  
[Drivers & Software](https://downloadcenter.intel.com/) 

## AMD AMF

AMD Advanced Media Framework is a light-weight, portable multimedia framework that abstracts away most of the platform and API-specific details and allows for easy implementation of multimedia applications using a variety of technologies, such as DirectX 11, OpenGL, and OpenCL and facilitates an efficient interop between them.

#### Supported Accelerations
The following accelerations are currently supported by Emby.
Please note that Emby may not support all accelerations offered by the hardware 
and that not all hardware devices will support all accelerations.

- Encoders
  - H.264 (AVC)

#### Hardware Requirements
The AMF framework is compatible with most recent Radeon GPUs starting 
with the Southern Islands family and APUs of the Kabini, Kaveri, Carrizo 
families and newer.

#### Required Setup Steps

Install the latest Radeon Software directly from AMD's website: 
[AMD Drivers & Support](https://www.amd.com/en/support) 
It is not required to install the AMF SDK.
The minumum required software version is: 
**AMD Radeon Software Crimson Edition 16.7.3 (16.30.2311)** 

#### Remarks

- Emby currently **does not support** headless operation with AMD AMF
  You will either need to connect a physical monitor to the video output
  or you can acquire a "dummy monitor plug" to make the GPU think that 
  a monitor is connected
- AMD AMF acceleration **does not work** when Emby is run as a Windows service

``Note: Support for headless mode is planned for the future``

#### Further Reading
[AMD Advanced Media Framework](https://gpuopen.com/gaming-product/advanced-media-framework/)  
[AMF SDK](https://github.com/GPUOpen-LibrariesAndSDKs/AMF)  
[AMD Drivers & Support](https://www.amd.com/en/support)  

## Microsoft DXVA
DirectX Video Acceleration (DXVA) is an Microsoft API for using hardware 
acceleration to speed up video processing. Software codecs and software 
video processors can use DXVA to offload certain CPU-intensive operations 
to the GPU.
DXVA supports video decoding only, no encoding.

#### Supported Accelerations
The following accelerations are currently supported by Emby.
Please note that Emby may not support all accelerations offered by the hardware 
and that not all hardware devices will support all accelerations.

- Decoders
  - H.264 (AVC)
  - H.265 (HEVC)
  - MPEG2
  - VC1

#### Hardware Requirements
DXVA supports graphics devices from different vendors, including Nvidia, Intel and AMD.

#### Required Setup Steps

DXVA is a Windows component, and supposed to work with the drivers that are 
included in Windows. 
Installing the latest drivers from the manufacturers' websites might still be a good idea.

#### Remarks

- Emby currently **does not support** headless operation with DXVA2
  You will either need to connect a physical monitor to the video output
  or you can acquire a "dummy monitor plug" to make the GPU think that 
  a monitor is connected
- DXVA2 acceleration **does not work** when Emby is run as a Windows service

``Note: Support for headless mode is planned for the future``

#### Further Reading
[About DXVA](https://docs.microsoft.com/en-us/windows/desktop/medfound/about-dxva-2-0)
