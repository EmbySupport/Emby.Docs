---
uid: Emby-Linux-FAQ
title: Emby Linux FAQ
---

[!INCLUDE [feature-start-animation](../../includes/beta-warning.md)]


### Where can I find the log files?

There are two ways:

1. **From within the application**
   - Go to settings: On the home view, click on the gear icon at the right top
   - In the navigation menu, choose "About"
    This is usually the topmost item. If you are admin of the Emby Server, you might see the server dashboard first and the section with the About entry needs to be expanded first
   - On the About page, switch to the "Log Files" tab
   - Click on one of the log files
2. **From the file system**
   - You can find the log files in the following directory  
    `~/.config/Emby Client Beta/cache/logs`
   - NOTE: This location may change during the beta or later


### I'm experiencing stuttering video playback, what can I do?

First of all, make sure you haven't chosen "High Quality" under **Video Player** settings >> **Video Quality**. Also, don't use "Customize" but try both the "Balanced" and the "Efficiency" presets.  
Then, use appropriate Linux tools for checking CPU and GPU usage.
Look at the Media Info on the item detail screen at the bottom and check whether the video has a high bitrate (> 20,000 Mbps).  
Open Stats for Nerds and see whether it's DirectPlay or Transcoding.  
Check your monitor configuration to see whether it runs at a high refresh rate.


### On the video quality settings page there are multiple presets. How can I know which settings are applied by each preset?

You can see the detail options applied by a preset by selecting one of the presets first and switching to Customize directly after.  
Switching to Customize keeps the values of the previously selected preset. This allows you to see how options are set by each preset.

### I am changing the subtitle style settings, but it doesn't seem that they have any effect.

There can be multiple reasons for this:

- The subtitles are "graphic" subtitles.
  The appearance of those cannot be changed.
  Typical subtitle formats using bitmaps are: DVDSub DVBSub, PGS/HDMV Subtitles
- The subtitles are SSA/ASS subtitles
  Those subtitles have built-in styling which cannot be overridden

### I have selected the High Quality preset in the video quality options, why doesn't it use hardware acceleration?

Short: While it does not perform hardware decoding and filtering, everything at the video presentation side (rendering on screen) is done by GPU shaders. This includes scaling, tone mapping and possibly subtitle overlay.

Long: On the decoding side, sw decoding can provide better quality, also you get the best deinterlacing by sw implementations, other filtering (e.g. dynamic bounds detection) works only with sw filtering. The best scaling is achieved by using GPU shaders (which happens at the end of the chain).
When doing sw filtering and scaling only at the end, then there's no advantage in using hw decoding. The computational effort weighs less than the data transfer between CPU and GPU memory.  
Actually, hw decoding is generally a bit overestimated. CPUs can do that easily as well. The main advantage of hw decoding is the avoidance of data transfer between GPU and CPU mem, when further processing happens in GPU memory. But hw decoding and just downloading it back to CPU memory right after it, is worse than doing CPU decoding using CPU memory right away. That's why there's no hw decoding in case of the high-quality mode. This mode is for achieving the best quality without compromise and without caring about efficiency and energy consumption.  
But this doesn't mean that the GPU isn't used: it's used for tone mapping and scaling and there are some scaling modes to choose which can get your GPU really hot.  
The energy efficient mode entirely disables the shader-based scaling and does the scaling in hardware (which is deemed to be of lower quality than shader-based scaling), and also maintains a full hardware processing pipeline (never does copying between GPU and CPU).  
In balanced mode, sw filtering is being used as well as shader-based scaling, but it uses hw decoding and in certain cases (when the video is much larger than the resolution of the current display) it downscales in hardware to reduce the amount of data while the eventual scaling is still done by GPU shaders (but at less load because of smaller video frames to scale).

