---
uid: Server-Transcoding-Advanced-Mode
title: "Advanced Mode"
---

Advanced Mode configures the devices themselves, rather than only choosing between them. Every detected
device gets its own configuration, the order they are listed in decides which is tried first, and each one
can be restricted to the kinds of operation it should handle.

What it does not do is change how the graph is shaped: it remains a list of devices with software
transcoding at the end, and the software fallback cannot be altered. Composing the decision itself -
containers, load balancing, failure points, custom fallback paths - is [Expert Mode](Expert-Mode.md).

## Differences from Basic to Advanced Mode

- Multiple GPUs can be configured and each can be restricted to specific operations like offline conversion, Live TV transcoding or playback transcoding
- A GPU configuration can be restricted to certain codecs (encoders and decoders)
- The [GPU context type](xref:Learn-Hardware-Frame-Surfaces) can be selected for GPUs which are supporting more than one, like for example
  - [VAAPI](xref:Learn-Hardware-Linux-VAAPI) vs. [QSV](xref:Learn-Hardware-Intel-QSV) for Intel GPUs on Linux
  - [AMF](xref:Learn-Hardware-AMD-AMF) vs. [Vulkan](xref:Learn-Hardware-Vulkan) for AMD GPUs
  - [CUDA](xref:Learn-Hardware-NVIDIA-CUDA) vs. Vulkan for NVIDIA GPUs
- Encoding parameters for hardware encoders can be set individually for each GPU and codec
- [Tone mapping filters](xref:Learn-Tone-Mapping-HDR-to-SDR) can be selected and configured for each GPU
- GPUs can be re-ordered to change their priority

## Priority

The devices are tried from top to bottom, so their order is their priority. A device is moved with the
**Move** command on the node itself, which then offers the positions it can be moved to.

Software transcoding stays at the end and cannot be moved, because it is the fallback - see
[Fallback Paths](Expert-Fallback-Paths.md#fallback-handling-in-basic-and-advanced-modes).

## Conditions

Each node can be restricted to certain kinds of operation, using the **Conditions** command. Advanced Mode
offers a simple list of the operation kinds:

- **Conversions** - offline conversions, not related to an active playback session
- **Live TV** - transcoding of Live TV
- **Playback** - transcoding for an active playback session
- **HLS Playback** - HLS transcoding for an active playback session
- **Live Stream** - transcoding of a live stream for an active playback session - a source without an end,
  such as a TV channel or a recording that is still in progress

All kinds apply until you exclude one. A node whose conditions exclude the operation being evaluated is
passed over, and the next node is tried.

Expert Mode replaces this list with a filter builder that can also match on source and output codec, on
processing steps such as tone mapping, and on user and library - see
[Node Conditions](Expert-Conditions.md).

## Device Configuration

The **Configure** command on a node opens everything about how that device is used:

- **GPU context type**, where the device offers more than one. The choice matters: contexts differ in
  maturity, in which filters they support and sometimes in which operations succeed at all. See
  [Hardware Acceleration](../hardware/Overview.md) for what each vendor offers
- **Encoders**, per output codec, along with the encoding parameters for the selected encoder - see
  [Encoders](encoders/Encoders.md)
- **Decoders**, per source codec
- **Tone mapping**, selected and configured per device for each kind of HDR - see
  [Filters](filters/Filters.md)
- **Subtitles** - how text and graphic subtitles are burned into the video when that is necessary - see
  [Subtitle Burn-In](Subtitle-Burn-In.md)

Anything left alone keeps its automatic default, and stays in step with it if that default later changes -
see [Delta Storage](Transcoding-Configuration.md#delta-storage).

## Switching Devices Off

Disabling a node moves it out of the graph to the bottom, so that what is actually in use stays readable at
a glance. Its configuration is kept, and switching it back on restores it. In Expert Mode disabled nodes
keep their position instead.

## Devices That Are No Longer There

A configuration for a device that has since become unavailable is still shown, so you can see that it
exists. When the configuration is next saved, those devices are removed automatically. Expert Mode keeps
them instead and leaves removing them to you.

## Remote GPUs

GPUs of remote transcoding hosts appear as devices of their own. Newly detected ones are added switched
off - switch them on to use them. While a host is switched off, its devices show *Host disabled*. Live TV
never uses a remote GPU. See [OmniTranscode™](../operations/OmniTranscode.md).

## Saving

Advanced Mode keeps a configuration history and asks for a name when saving - see
[Saving](Transcoding-Configuration.md#saving).
