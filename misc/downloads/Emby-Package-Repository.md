---
uid: Emby-Package-Repository
title: Emby Package Repository
---

# Emby Package Repository (Linux)

This documentation explains how to add the Emby package repository on Linux and install packages.

## Choose an installation method

### Universal installer

Use this if you want a guided (interactive) installer that:

- detects your package manager automatically (APT, DNF, Zypper, Pacman)
- avoids running as root until it needs to make system changes
- can be used non-interactively via environment variables

See: [Linux Universal Installer](Emby-Pkg-Installer.md)


### Manual setup (per package manager)
Use this if you prefer to configure the repository yourself:

- APT (Debian/Ubuntu/Mint): [Emby Pkg APT](Emby-Pkg-APT.md)
- DNF (Fedora/RHEL/CentOS): [Emby Pkg DNF](Emby-Pkg-DNF.md)
- Zypper (openSUSE/SLE): [Emby Pkg Zypper](Emby-Pkg-Zypper.md)
- Pacman (Arch/derivatives): [Emby Pkg Pacman](Emby-Pkg-Pacman.md)

## Channels

Emby publishes two independent channels:

- `stable`: recommended for most users
- `beta`: preview builds

Each guide contains stable/beta instructions.

## Package names

Common package IDs you may see:

- `emby-server`
- `media.emby.client` (stable client)
- `media.emby.client.beta` (beta client)

Available packages vary by distribution and architecture.
