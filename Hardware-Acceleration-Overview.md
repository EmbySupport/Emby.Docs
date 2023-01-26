Emby supports a broad range of hardware accelerated video transcoding methods on its supported platforms:

## Windows

Emby supports the following [hardware acceleration variants on Windows](Hardware-Acceleration-on-Windows)

- **Nvidia NVDEC & NVENC**  
API for video encoding and decoding acceleration using Nvidia GPUs

- **Intel QuickSync Video**  
 Intel's brand for its dedicated video encoding and decoding hardware 
 core

- **AMD AMF**  
 AMD Advanced Media Framework - multimedia API  AMD hardware for 
 real-time processing of multimedia

- **Microsoft DXVA**  
 Microsoft DirectX Video Acceleration API - hardware independent API 
 for hardware accelerated video decoding

## Linux

Emby supports the following [hardware acceleration variants on Linux](Hardware-Acceleration-on-Linux)

- **Nvidia NVDEC & NVENC**  
API for video encoding and decoding acceleration using Nvidia GPUs

- **VA API]**  
Video Acceleration API for Linux is supported by several device manufacturers

- **Intel QuickSync Video**  
 Intel's brand for its dedicated video encoding and decoding hardware 
 core

## Android

Emby supports the following [hardware acceleration variants on Android](Hardware-Acceleration-on-Android)

- **Android MediaCodec**  
MediaCodec is Android's integrated API for video de- and endoding. 

- **OpenMax**  
OpenMax is an API specification covering various aspects of media acceleration. On Android it is the standard API for codec implementations while applications are typically using MediaCodec

## Troubleshooting

**I've enabled hardware acceleration but CPU usage is still very high when transcoding and PGS or DVD subtitles are enabled.**

In many cases these subtitle formats will need to be burned into the video on the fly with transcoding. Most GPU's do not support this and as a result there will be some significant CPU involvement. This is a very taxing process for even a powerful server, and it's generally something you want to avoid. Here are the best ways to avoid burning in subtitles:
* Turn off the subtitles prior to playback using the pre-playback subtitle selection menu
* Use external text-based subtitles instead, such as .srt files. Emby Server's subtitle download features can help automate the process of acquiring these.
* Use an Emby app that can direct play these subtitle formats without transcoding, such as Emby Theater, Android, or iOS.