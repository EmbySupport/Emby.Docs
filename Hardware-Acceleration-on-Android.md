Emby supports the following hardware acceleration variants on Android

- **Android MediaCodec**  
MediaCodec is Android's integrated API for video de- and endoding. 

- **OpenMax**  
OpenMax is an API specification covering various aspects of media acceleration. On Android it is the standard API for codec implementations while applications are typically using MediaCodec

This applies to Emby as well. Emby supports hardware accelerated codecs through the MediaCodec API.
We're mentioning OpenMax here to avoid confusion in that matter, because codecs are often named like "h26x.OMX.Google.encoder.*", where OMX is indicating the API of the codec implementation, even when accessed through the MediaCodec API.


## Android MediaCodec

Android MediaCodec API covers a wide range of hardware accelerated codec implementation. 
In case of Android, it is up to the device manufacturer to deliver appropriate codec implementations (or not).

#### Supported Accelerations
The following codec are currently supported by Emby on Android.
Please note that Emby may not support all accelerations offered by the hardware 
and that not all devices will support all accelerations.

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
Hardware acceleration on Android is depending on the actual hardware and on the support of device manufacturer.
Due to the huge number of available devices it is hardly possible to establish and maintain compatibility listings. On a more general basis we can say that we have successfully run and tested Emby Server with accelerated codecs from:
- Nvidia (Tegra)
- Samsung (Exynos)
- AmLogic
- RealTek
(this does not mean that it will work with every device from each of those manufacturers)

#### Setup and Hardware Detection

There is no setup required. Emby will automatically detect the available hardware codecs. 
These can be viewed by navigating to the Transcoding page on the server dashboard and choosing "Advanced" in the acceleration type dropdown list.


