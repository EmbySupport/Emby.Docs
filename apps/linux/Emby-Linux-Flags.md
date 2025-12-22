---
uid: Emby-Linux-Flags
title: Emby Linux: Commandline Flags
---

# Emby Linux: Commandline Flags

[!INCLUDE [feature-start-animation](../../includes/beta-warning.md)]

The commandline flags documented below might be useful to fix certain issues you may encounter when testing.

**IMPORTANT:** In case you are encounter an issue which can be fixed by applying one of those flags, please let use know about it, as the intention is having everything to be working right out-of-the-box, without needing to apply any flags.


## How to use

In a terminal window, navigate to the install location of the Emby Linux app. 
In most cases, this will be `/opt/Emby-Beta`. The executable is named `Emby`.

**Example**

```bash
cd /opt/Emby-Beta
./Emby -nompv
```

## Available Flags

#### nompv

Disables playback via MPV player in a separate window and switches Emby Linux to use the HTML video player instead.

```bash
./Emby -nompv
```

#### persistplayer

In case you experience player crashes, specifically after the first or when starting a 2nd playback, this flag may help. It loads the player once and keeps it loaded until application exit.

```bash
./Emby -persistplayer
```

#### nojokermode

Keeps the video window visible all the time. Only useful for diagnosing.

```bash
./Emby -nojokermode
```

#### nossinhibitor

Disables automatic inhibition of screensavers or sleep mode during playback.
Use case is diagnosing errors during playback (ruling out the screen-saver inhibition).

```bash
./Emby -nossinhibitor
```

#### usenormalwindow

Changes the type of the video window. Should only be used when instructed to.

```bash
./Emby -nossinhibitor
```

#### stack1, stack2, stack3, stack4, 

The application uses different ways for window stacking (z-order).
If you encounter issues with incorrect stacking you can try all the available modes.

Example:

```bash
./Emby -stack2
```


#### mini1, mini2, mini3, mini4, 

The application uses different ways for handling the video window on minimize and unminimize.
If you encounter issues with incorrect minimize behaviour you can try all the available modes.

Example:

```bash
./Emby -mini3
```
