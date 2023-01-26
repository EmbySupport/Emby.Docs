Emby supports the following hardware acceleration variants on Linux

- **[Nvidia NVDEC & NVENC](#nvidia-nvdec-nvenc)**  
API for video encoding and decoding acceleration using Nvidia GPUs

- **[VA API](#va-api)**  
Video Acceleration API for Linux is supported by several device manufacturers

- **[Intel QuickSync Video](#intel-quicksync-video)**  
 Intel's brand for its dedicated video encoding and decoding hardware 
 core

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

Install the latest drivers for your Nvidia hardware either directly from 
[Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx) page
or from the driver repository of the respective Linux distribution.
The procedure may vary by distribution.
The minimum required driver version on Linux is **390.25**  

#### Remarks

- Emby supports headless operation for Nvidia  
  It is not required to connect a monitor

#### Further Reading
[Nvidia Video Codec SDK](https://developer.nvidia.com/nvidia-video-codec-sdk)  
[GPU Support Matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix)  
[Nvidia Driver Downloads](https://www.nvidia.com/Download/index.aspx)  
[NVENC](https://en.wikipedia.org/wiki/Nvidia_NVENC), 
[NVDEC](https://en.wikipedia.org/wiki/Nvidia_NVDEC)

## VA API

VAAPI (Video Acceleration API) is an open-source library and API specification, which provides access to graphics hardware acceleration capabilities for video processing. It consists of a main library and driver-specific acceleration backends for each supported hardware vendor.

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

- **Intel**
  - Information about supported Intel CPUs with integrated graphics can be found here:
[Intel Video and Audio for Linux](https://01.org/vaapi)

- **AMD**
  - [AMDGPU-PRO Driver for Linux](https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-amdgpupro)
  - [Radeon™ Software for Linux](https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-18-40)

- **Other Hardware Supporting VA API**
  - [Supported hardware and drivers](https://en.wikipedia.org/wiki/Video_Acceleration_API#Supported_hardware_and_drivers)

#### Required Setup Steps

##### Intel

The latest Intel drivers are included with Emby server.

##### AMD

[Radeon™ Software for Linux® Installation](https://www.amd.com/en/support/kb/faq/amdgpu-installation)

#### Further Reading

[Video Acceleration API](https://en.wikipedia.org/wiki/Video_Acceleration_API)
[Intel Video and Audio for Linux](https://01.org/vaapi)

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
can be found under the following links: 

- [Driver Support Matrix for Intel® Media SDK and OpenCL™](https://software.intel.com/en-us/articles/driver-support-matrix-for-media-sdk-and-opencl)
- [Hardware decoding and encoding](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding).
- [GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration)).

#### Required Setup Steps

The steps for installing the Intel Media SDK may vary depending on your actual system. Please follow the instructions appropriate for your actual setup which you can find here:

- [Getting Started Guide](https://software.intel.com/en-us/download/intel-media-server-studio-driver-sdk-for-linux-getting-started-guide)  
- [Generic Installation for Intel® Media Server Studio](https://software.intel.com/en-us/articles/generic-installation-for-intel-media-server-studio)  
- [Generic Linux* Intel® Media Server Studio Installation](https://software.intel.com/en-us/articles/how-to-setup-media-server-studio-on-secondary-os-of-linux)  
- [System Analyzer Utility for Linux](https://software.intel.com/en-us/articles/mss-sys-analyzer-linux)  

#### Further Reading
[Intel QuickSync Video](https://www.intel.com/content/www/us/en/architecture-and-technology/quick-sync-video/quick-sync-video-general.html)  
[Driver Support Matrix for Intel® Media SDK and OpenCL™](https://software.intel.com/en-us/articles/driver-support-matrix-for-media-sdk-and-opencl)  
[Codec Support by CPU Generation](https://en.wikipedia.org/wiki/Intel_Quick_Sync_Video#Hardware_decoding_and_encoding)  
[GPU Acceleration Capabilities](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Capabilities_(GPU_video_acceleration))  

