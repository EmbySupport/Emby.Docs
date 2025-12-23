---
uid: Emby-Windows-FAQ
title: Emby Windows FAQ
---

[Is this only a successor to the Windows Store app? What does it mean for Emby Theater Desktop?](#is-this-only-a-successor-to-the-windows-store-app-what-does-it-mean-for-emby-theater-desktop)

[Why can't you just leave Emby Theater Desktop as is and let me continue using it?](#why-cant-you-just-leave-emby-theater-desktop-as-is-and-let-me-continue-using-it)

[How can I launch the Emby app from the command line?](#how-can-i-launch-the-emby-app-from-the-command-line)

[How can I make the Emby app start automatically on Windows startup?](#how-can-i-make-the-emby-app-start-automatically-on-windows-startup)

[I'm experiencing stuttering video playback, what can I do?](#im-experiencing-stuttering-video-playback-what-can-i-do)

[On the video quality settings page there are multiple presets. How can I know which settings are applied by each preset?](#on-the-video-quality-settings-page-there-are-multiple-presets-how-can-i-know-which-settings-are-applied-by-each-preset)

[I have installed the app, but it doesn't look like it does in some of the screenshots.](#i-have-installed-the-app-but-it-doesnt-look-like-it-does-in-some-of-the-screenshots)

[To which folder do the downloaded files go when using the Download/Sync feature?](#to-which-folder-do-the-downloaded-files-go-when-using-the-downloadsync-feature)

[I am changing the subtitle style settings, but it doesn't seem that they have any effect.](#i-am-changing-the-subtitle-style-settings-but-it-doesnt-seem-that-they-have-any-effect)

[Will the Windows theme be made available in other Emby apps?](#will-the-windows-theme-be-made-available-in-other-emby-apps)

[Is there some other way to download and install the Windows App?](#is-there-some-other-way-to-download-and-install-the-windows-app)

[Why can't you provide an MSIX for download and manual installation?](#why-cant-you-provide-an-msix-for-download-and-manual-installation)

[Why are you forcing me to have a Microsoft account for downloading the app from the Microsoft Store?](#why-are-you-forcing-me-to-have-a-microsoft-account-for-downloading-the-app-from-the-microsoft-store)

[I have selected the High Quality preset in the video quality options, why doesn't it use hardware acceleration?](#i-have-selected-the-high-quality-preset-in-the-video-quality-options-why-doesnt-it-use-hardware-acceleration)

[The start animation is nice, but it takes a long time and the previous Windows & Xbox apps were starting up faster, can the animation be disabled?](#the-start-animation-is-nice-but-it-takes-a-long-time-and-the-previous-windows--xbox-apps-were-starting-up-faster-can-the-animation-be-disabled)


### Is this only a successor to the Windows Store app? What does it mean for Emby Theater Desktop?

The new Emby app for Windows supersedes and replaces both apps. Effective by the release date of the new Windows app, Emby Theater Desktop is now discontinued.



### Why can't you just leave Emby Theater Desktop as is and let me continue using it?

Emby Theater Desktop is not an isolated application. It is running the app code from an online URL to access our common code base which is full of specific code for this app. Sunsetting support for ET Desktop allows us to clean up and tighten our code base which in turn accelerates future development and allows us to introduce new features which were blocked due to incompatibility with the outdated browser engine in ET Desktop which is based on a years-old version of Electron.  
Its Chromium version has a wealth of security issues and the way of loading the app code via insecure http adds to that. https cannot be used as it wouldn't be possible to connect to Emby Servers without SSL.


### How can I launch the Emby app from the command line?

Simply type

```cmd
EmbyClientWinUI
```

on a command line or from the "Run" dialog (WIN+R).

The full path to this "execution alias" is:

```
C:\Users\<username>\AppData\Local\Microsoft\WindowsApps\EmbyClientWinUI.exe
```


### How can I make the Emby app start automatically on Windows startup?

This is simple to do with plain old Windows functionality, just a bit less accessible these days:

- Open **Windows Explorer**
- Enter this into the address bar:`%AppData%\Microsoft\Windows\Start Menu\Programs\Startup`
- Leave that Window open
- Open **Start Menu** >> **All Apps**
- Scroll down until you see the Emby app icon
- Drag-drop it into the Startup folder in the Explorer Window

Done!



### I'm experiencing stuttering video playback, what can I do?

First of all, make sure you haven't chosen **Video Player** settings >> **Video Quality**. Also, don't use "Customize" but try both the "Balanced" and the "Efficiency" presets.  
Then, look at the Windows Task Manager and check both CPU and GPU usage, and look for high values.  
Look at the Media Info on the item detail screen at the bottom and check whether the video has a high bitrate (> 20,000 Mbps).  
Open Stats for Nerds and see whether it's DirectPlay or Transcoding.  
Check your monitor configuration to see whether it runs at a high refresh rate (you can see that directly in the Emby app in the "Display Control" section.



### On the video quality settings page there are multiple presets. How can I know which settings are applied by each preset?

You can see the detail options applied by a preset by selecting one of the presets first and switching to Customize directly after.  
Switching to Customize keeps the values of the previously selected preset. This allows you to see how options are set by each preset.



### I have installed the app, but it doesn't look like it does in some of the screenshots.

These are showing the Windows theme as it's new and exclusive to the Windows app.
To enable the Windows theme, click the gear icon at the right top and choose **Setting**, then click **Display** and find the **Theme** setting.


### To which folder do the downloaded files go when using the Download/Sync feature?

Go to **Settings** >> **About**

There you will see the folder location as **Data Path**

Selection of a custom folder is planned for a future update.



### I am changing the subtitle style settings, but it doesn't seem that they have any effect.

There can be multiple reasons for this:

- The subtitles are "graphic" subtitles.
  The appearance of those cannot be changed.
  Typical subtitle formats using bitmaps are: DVDSub DVBSub, PGS/HDMV Subtitles
- The subtitles are SSA/ASS subtitles
  Those subtitles have built-in styling which cannot be overridden


### Will the Windows theme be made available in other Emby apps?

The Windows theme is exclusive to the Windows app. Its colors are controlled directly by Windows style settings, which are not available on other platforms. Also, it is not allowed to use the font (Segoe Variable) on websites or other platforms.  
The primary point, though, is that a crucial element of its appeal comes from the Mica background material in combination with translucency used in all the elements and colors. Without the background, it looks pretty boring actually.



### Is there some other way to download and install the Windows App?

No, the Windows Store is the only way to install



### Why can't you provide an MSIX for download and manual installation?

Because we rely on the store's updating abilities.Our delivery model requires frequent updates to the core application code. Instead of loadign the code from an online resource (which has numerous security implications), it has all its code on board now. The Windows store is the ideal choice for this, as it allows to deliver updates to the app in the background, without interrupting users' workflow by having them watch and confirm an installation procedure every few days or weeks.

So, the installation is not just about getting our app once installed on users' machines. The automatic updating via Windows Store is a crucial element of the concept which wouldn't work out when providing MSIX packages for manual installation, as that would cause installations to be almost always out-of -date.



### Why are you forcing me to have a Microsoft account for downloading the app from the Microsoft Store?

You do NOT need a Microsoft account. It is not required to be logged into the MS Store for downloading the Emby app.

See here for more details: https://emby.media/community/index.php?/topic/134058-why-does-emby-make-it-so-difficult-to-discover-media/page/5/#findComment-1408507


### I have selected the High Quality preset in the video quality options, why doesn't it use hardware acceleration?

Short: While it does not perform hardware decoding and filtering, everything at the video presentation side (rendering on screen) is done by GPU shaders. This includes scaling, tone mapping and possibly subtitle overlay.

Long: On the decoding side, sw decoding can provide better quality, also you get the best deinterlacing by sw implementations, other filtering (e.g. dynamic bounds detection) works only with sw filtering. The best scaling is achieved by using GPU shaders (which happens at the end of the chain).
When doing sw filtering and scaling only at the end, then there's no advantage in using hw decoding. The computational effort weighs less than the data transfer between CPU and GPU memory.  
Actually, hw decoding is generally a bit overestimated. CPUs can do that easily as well. The main advantage of hw decoding is the avoidance of data transfer between GPU and CPU mem, when further processing happens in GPU memory. But hw decoding and just downloading it back to CPU memory right after it, is worse than doing CPU decoding using CPU memory right away. That's why there's no hw decoding in case of the high-quality mode. This mode is for achieving the best quality without compromise and without caring about efficiency and energy consumption.  
But this doesn't mean that the GPU isn't used: it's used for tone mapping and scaling and there are some scaling modes to choose which can get your GPU really hot.  
The energy efficient mode entirely disables the shader-based scaling and does the scaling in hardware (which is deemed to be of lower quality than shader-based scaling), and also maintains a full hardware processing pipeline (never does copying between GPU and CPU).  
In balanced mode, sw filtering is being used as well as shader-based scaling, but it uses hw decoding and in certain cases (when the video is much larger than the resolution of the current display) it downscales in hardware to reduce the amount of data while the eventual scaling is still done by GPU shaders (but at less load because of smaller video frames to scale).



### The start animation is nice, but it takes a long time and the previous Windows & Xbox apps were starting up faster, can the animation be disabled?

While the animation is running, you can click on the "Hide" button in the bottom right corner of the window. You will see, though, that this doesn't accelerate startup. In fact, it is not that the app is waiting for the animation to finish, instead, the animation is only there to sweeten up the startup experience instead of just showing a spinning circle for the same duration.

Technical background: https://emby.media/community/index.php?/topic/131876-windows-xbox-app-beta/page/6/#findComment-1398478
