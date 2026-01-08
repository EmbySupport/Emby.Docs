---
uid: Emby-Pkg-Pacman
title: "Manual Repo Setup: Pacman"
---

# Manual setup: Pacman

## Arch Linux / derivatives

This guide explains how to configure the Emby Pacman repository manually (without using `get.sh`).

## Prerequisites

You need:

- `pacman`
- `curl`
- `gpg` (usually present; used to extract the key fingerprint)
- `pacman-key`

## Channels and architecture

Emby publishes two channels:

- `stable` (repo name: `emby-stable`)
- `beta` (repo name: `emby-beta`)

The repository URL also depends on your architecture:

- `x86_64` (most desktop/server installs)
- `aarch64` (ARM64)

The published server format is:

- `https://pkg.emby.media/pac/<channel>/os/<arch>`

Example (stable, x86_64):

- `https://pkg.emby.media/pac/stable/os/x86_64`

---

## 1) Determine your architecture

```bash
uname -m
```

Use:

- `x86_64` → `x86_64`
- `aarch64` (or `arm64`) → `aarch64`

---

## 2) Import and locally sign the Emby signing key

Pacman requires repository signing keys to be present in the pacman keyring and locally trusted.

Key URL:

- `https://pkg.emby.media/keys/emby-public.asc`

### Initialize keyring (only if needed)

```bash
sudo pacman-key --init
sudo pacman-key --populate
```

### Download key and add it to pacman

```bash
tmpkey="$(mktemp)"
curl -fsSL https://pkg.emby.media/keys/emby-public.asc -o "$tmpkey"
sudo pacman-key --add "$tmpkey"
```

### Extract fingerprint and locally sign it

```bash
FPR="$(gpg --show-keys --with-colons "$tmpkey" | awk -F: '/^fpr:/ {print $10; exit}')"
sudo pacman-key --lsign-key "$FPR"
rm -f "$tmpkey"
```

---

## 3) Add the repository stanza to `/etc/pacman.conf`

Edit `/etc/pacman.conf` and add one of the following blocks.

### Stable channel

(Replace `<arch>` with `x86_64` or `aarch64`)

```ini
[emby-stable]
Server = https://pkg.emby.media/pac/stable/os/<arch>
SigLevel = Required DatabaseRequired
```

### Beta channel

```ini
[emby-beta]
Server = https://pkg.emby.media/pac/beta/os/<arch>
SigLevel = Required DatabaseRequired
```

---

## 4) Refresh package databases

```bash
sudo pacman -Syy
```

---

## Verify repository configuration

Confirm Pacman sees packages from the repo:

```bash
pacman -Sl emby-stable 2>/dev/null | head
```

(or for beta)

```bash
pacman -Sl emby-beta 2>/dev/null | head
```

Show package info:

```bash
pacman -Si emby-server
```

---

## Install / upgrade / uninstall examples

Install server:

```bash
sudo pacman -S emby-server
```

Upgrade system packages:

```bash
sudo pacman -Syu
```

Uninstall:

```bash
sudo pacman -Rns emby-server
```

---

## Remove the repository

1) Remove the `[emby-stable]` or `[emby-beta]` section from `/etc/pacman.conf`.
2) Refresh databases:

```bash
sudo pacman -Syy
```

(You can keep the key in the pacman keyring; removing it is optional.)
