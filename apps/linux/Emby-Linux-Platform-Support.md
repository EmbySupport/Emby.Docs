---
uid: Emby-Linux-Platform-Support
title: Emby Linux: Platform Support
---

> [!WARNING]
> The information in this document is about a pre-release application. All the provided details are subject to being changed without notice. 

# Emby Linux: Platform Support
## Introduction

The Linux ecosystem is highly heterogeneous - not only because of the wide variety of distributions, but even more because of Desktop Environments, different distro + DE combinations, and the choice of display server (X11 vs. Wayland).
For the Emby Client application, it is not feasible for us to support all of these variations in a reasonable and sustainable way. We have to make clear cuts between what is manageable and what is not.
This article explains our goals and current scope: which hardware and software environments we are targeting to run the Emby Client app for Linux reliably.

### DISCLAIMER

This document is an informational description of our current testing focus and intended support boundaries. It is not a contract, a warranty, or a legally binding promise of support.
"Supported" in this context means that we actively test and prioritize the listed environments. It does not guarantee that the application will be free of defects, compatible with every configuration, or suitable for every use case.

Linux systems can differ significantly even within the same distribution and version (kernel versions, Mesa/NVIDIA driver versions, compositor behavior, audio stack, sandboxing, packaging differences, and third-party modifications). Because of that, issues may occur even on supported targets, and behavior may change with updates to the OS, drivers, or desktop environment.

Our support focus may change over time. We may add, move, or remove targets between tiers, change minimum versions, or revise limitations based on development priorities, available test coverage, and real-world feedback. For pre-release software, these changes can happen without notice.

For environments listed as Unsupported, we may decline investigations, troubleshooting, or implementation work - even if the application happens to run. For environments listed as Extended Tier, we will generally try to help, but fixes are best-effort and may be deprioritized or declined if the effort is disproportionate or the root cause lies outside our control (e.g., upstream bugs, driver limitations, or platform behavior).


## Support Levels

This document introduces the following three support levels for categorization further down:

- Primary Tier
- Extended Tier
- Unsupported

### Primary Tier

These are the environments that are used in development and on whch the software is regularly tested.
We are aiming to have the Emby client application working continuously in a stable and reliable way.  
Fixing issues and bugs on these targets will always be given priority over other targets (like from the Extended Tier)

### Extended Tier

Environments from the extended tier are outside of the core focus. 
We are trying to get the Emby client app working on these, but rather on a best-effort basis. If it turns out that fixing or addressing a specific issue would require an unusually high amount of work, we may choose not to implement it.  

### Unsupported

Unsupported means that it may work or may not work, but users are on their own.  
We will not perform any kind of work nor discuss or answer any questions about it, other than stating that it's not supported.


## Support Declarations

### Linux Distributions and Versions

- Primary Tier
  - Ubuntu
	- 22.04, 24.04, 25.10 and later
  - Debian
	- 11, 12, 13 and later
- Extended Tier
  - Arch Linux
	- Current (rolling)
  - Fedora
	- 42, 43 and later
  - Linux Mint
	- 22, 22.1, 22.2 and later
  - OpenSUSE Tumbleweed
	- Current (rolling)
  - Manjaro
	- Current (rolling)
  - SteamOS
	- 3.7.x and later
	- Game Mode is unsupported!

#### Notes

- Any distro not in this list is unsupported.


### Desktop Environments

- Primary Tier
  - KDE Plasma
  - Gnome
  - XFCE
- Extended Tier
  - Cinnamon
  - Mate
  - LXQt

#### Notes

- Any DE not in this list is unsupported.


### Display Servers

- Primary Tier
  - X11
  - Wayland via Xwayland

#### Notes

- Native Wayland is unsupported.


### CPU Architectures

- Primary Tier
  - x86-64
- Extended Tier
  - arm64 (limited)

#### Notes

- Hardware acceleration for ARM64 devices is not available yet (see below), which limits the value of running the app on ARM64 devices at this time. 

### GPU Hardware and Hardware Acceleration

- Primary Tier
  - Intel via VAAPI
  - AMD via VAAPI
- Extended Tier
  - Nvidia

#### Notes

- Nvidia is planned to become Primary Tier after more testing
- Video Hardware acceleration for ARM64 devices is planned for a future update




