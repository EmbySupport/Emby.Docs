---
uid: Emby-Pkg-APT
title: "Manual Repo Setup: APT"
---

# Manual setup: APT 

## Debian / Ubuntu / Linux Mint

This guide explains how to configure the Emby APT repository manually (without using `get.sh`).

## Prerequisites

You need:

- `curl`
- `ca-certificates`
- `gnupg` (only needed if you want to inspect keys; the steps below use a `.gpg` keyring directly)

## Channels

Emby publishes two APT channels:

- `stable` (recommended)
- `beta`


---

## Stable channel

### 1) Install the signing key

The APT setup uses a keyring file:

- Key URL: `https://pkg.emby.media/keys/emby-public.gpg`
- Keyring path: `/etc/apt/keyrings/emby-public.gpg`

```bash
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://pkg.emby.media/keys/emby-public.gpg -o /etc/apt/keyrings/emby-public.gpg
sudo chmod 0644 /etc/apt/keyrings/emby-public.gpg
```

### 2) Add the repository source (Deb822 `.sources`)

For stable, the repo publishes a Deb822 source file at:

- `https://pkg.emby.media/apt/emby.sources`

Create:

- `/etc/apt/sources.list.d/emby.sources`

```bash
sudo curl -fsSL https://pkg.emby.media/apt/emby.sources -o /etc/apt/sources.list.d/emby.sources
```

This file contains (for reference):

```text
Types: deb
URIs: https://pkg.emby.media/apt/
Suites: stable
Components: main
Architectures: amd64 arm64 armhf
Signed-By: /etc/apt/keyrings/emby-public.gpg
```

### 3) Refresh package indices

```bash
sudo apt-get update
```

---

## Beta channel

### 1) Install the signing key

Same key as stable:

```bash
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://pkg.emby.media/keys/emby-public.gpg -o /etc/apt/keyrings/emby-public.gpg
sudo chmod 0644 /etc/apt/keyrings/emby-public.gpg
```

### 2) Add the repository source

Create:

- `/etc/apt/sources.list.d/emby-beta.sources`

```bash
sudo curl -fsSL https://pkg.emby.media/apt/emby-beta.sources -o /etc/apt/sources.list.d/emby-beta.sources
```

### 3) Refresh package indices

```bash
sudo apt-get update
```

---

## Verify repository configuration

Show which versions APT sees and which repo they come from:

```bash
apt-cache policy emby-server
```

You should see `pkg.emby.media` and the chosen suite (`stable` or `beta`) in the output.

List packages from the repo (basic approach):

```bash
apt-cache search emby
```

---

## Install / upgrade / uninstall examples

Install server:

```bash
sudo apt-get install emby-server
```

Upgrade:

```bash
sudo apt-get update
sudo apt-get upgrade
```

Uninstall:

```bash
sudo apt-get remove emby-server
```

---

## Remove the repository

Stable:

```bash
sudo rm -f /etc/apt/sources.list.d/emby.sources
sudo apt-get update
```

Beta:

```bash
sudo rm -f /etc/apt/sources.list.d/emby-beta.sources
sudo apt-get update
```

(You can keep the keyring file in `/etc/apt/keyrings/` if you plan to re-add the repo later.)
