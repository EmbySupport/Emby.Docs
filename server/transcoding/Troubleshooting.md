---
uid: Server-Transcoding-Troubleshooting
title: "Transcoding Troubleshooting"
---

# Transcoding Troubleshooting

## Why Is My Media Transcoding?

If the question is why transcoding is happening at all, rather than why it is failing or slow, see
[Why Is My Media Transcoding?](Why-Media-Transcodes.md).

## Start with One Playback

Choose one item that reproduces the problem and note the time, client, selected subtitles and playback
quality. While it plays, open **Transcoding → Operations → Activity** to see which host and device are
doing the work. Then open the matching [FFmpeg log](operations/Logs.md#ffmpeg-logs).

Change one setting at a time, save the configuration, and start a new playback to compare the result.
Changes to the graph apply when a new transcoding operation is evaluated.

## A GPU Is Missing

1. Open [Detection Logs](operations/Logs.md#detection-logs) and select the correct host. Read its latest
   detection log for the device and any reported errors.
2. Check the [GPU Setup](../setup/gpu-setup/GPU-Setup.md) instructions for that host's operating system.
   Confirm that the required driver is installed and that the Emby Server account can access the device.
3. For a remote GPU, check that the host is enabled and prepared. Use
   [Troubleshoot](operations/OmniTranscode.md#troubleshooting-a-host) on that host if preparation failed.
4. If detection found the GPU but it is not used, check the configuration: Basic Mode does not use remote
   GPUs, and Advanced Mode adds newly detected remote GPUs switched off.

## Software Is Selected Instead of a GPU

In the FFmpeg log, find **Transcoding configuration**, **Configured**, **Effective** and **Selected**.
The [evaluation results](configuration/Expert-Graph-Evaluation.md#reading-the-result-in-the-log) explain
why each node was selected or passed over.

- If the GPU is absent from **Effective**, check whether it or its remote host is disabled or unavailable.
- If it appears but is passed over, read its result and the details below it. Check its conditions, encoder
  and decoder choices, subtitle burn-in settings, and any load limits. `EncoderHardwareNotAllowed` means
  hardware encoding requires an active Emby Premiere subscription.
- If the GPU was selected first and software was used later, look for *Previous transcoding attempt
  failed* and the error from that attempt. This is a fallback after failure, rather than an initial
  selection of software.

Software decoding or a software filter can also be used while encoding remains on the GPU. Check which
stage is using software before changing the device selection.

## A Fallback Does Not Run or Also Fails

1. Read the **Fallback configuration** section of the log. In Expert Mode, check that the intended fallback
   node is marked as a fallback point, comes after the initially selected node, and matches the operation's
   conditions and capabilities. A failure point can stop further fallback selection.
2. Check when the failure happened. Fallback applies to failed startup attempts; it does not restart a
   transcode that already started successfully and failed later. The **Live TV** operation kind uses only
   the selected node; playback classified as **Live Stream** can use playback fallbacks.
   See [When an Attempt Fails](configuration/Expert-Graph-Evaluation.md#when-an-attempt-fails).
3. If several attempts ran, inspect each attempt's FFmpeg log. Look for source-access or temporary-folder
   errors shared by the attempts, and check access from the host used for each attempt.

See the [worked graph example](configuration/Expert-Graph-Evaluation.md#example-try-another-context-before-software) for an initial
selection followed by hardware and software fallbacks.

## Playback Is Slow or Buffers

1. Check the selected host, device and encoder in Activity and the FFmpeg log. A software fallback may
   explain a change in performance.
2. Check the transcoding speed while FFmpeg is actively encoding. Playback needs it to keep ahead of real
   time (1×). Pauses caused by [transcoding throttle](Settings.md#transcoding-throttle) are expected when
   sufficient output is already buffered.
3. Compare the same item with other transcodes stopped. If speed improves, the host may be at its practical
   capacity for that workload. Configured concurrency limits do not guarantee a particular speed.
4. Try a lower playback quality. If subtitles are selected, briefly compare with them off to determine
   whether subtitle processing is contributing. Review the chosen encoder and tone mapping settings if
   they were customized.
5. If encoding stays ahead but playback still buffers, check media access, temporary-storage performance
   and the connection to the client. Remote transcoding also depends on the connection between the server
   and remote host.

## Hardware Acceleration Fails with Remote Desktop

See [Hardware Acceleration fails with RDP](Hwa-Fails-with-RDP.md).

## Logs

Whether and how a device was detected is recorded in the [Detection Logs](operations/Logs.md#detection-logs),
and what happened during a transcode in the [FFmpeg Logs](operations/Logs.md#ffmpeg-logs).

## Further Reading

<xref:Learn-Playback-Transcode-Logs>  
<xref:Learn-Playback-Bottlenecks>
