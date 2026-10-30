

<video src="../../../videos/Display-Control.mp4" controls="controls" style="max-height:640px; min-height: 200px; max-width: 100%;">
</video>

## Features

- Detects GPUs, connected displays and the connection type
- Detects possible [refresh rates](xref:Learn-Display-Refresh-Rate) for each connection  
  (depends on GPU capabilities, display capabilities, connection type, current resolution, current color mode)
- Detects availability of [HDR mode](xref:Learn-Display-HDR-Capabilities) for each connection
- Detects the display on which the Emby app is currently being shown
  (Windows app only)
- Dynamically updates the settings view when changes are made to OS settings or displays are connected/disconnected
- Allow manual switching of refresh rate and HDR mode (three-dot menu)
- Automatic [switching of refresh rate](xref:Learn-Display-Frame-Rate-Matching) and HDR mode on playback start can be enabled independently and separately for each display  
  This will only be applied to the display on which the app is currently shown
- Revertion of refresh rate and HDR mode on playback stop can be disabled to reduce display mode changes (which can take a few seconds)

## How to...

- **...access the Display Control settings?**  
Go to Settings (Gear icon), in the left sidebar choose "Display Control"