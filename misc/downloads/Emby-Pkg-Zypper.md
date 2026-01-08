---
uid: Emby-Pkg-Zypper
title: "Manual Repo Setup: Zypper"
---

# Manual setup: Zypper

## openSUSE / SLE

This guide explains how to configure the Emby RPM repository manually for Zypper-based systems (without using `get.sh`).

## Prerequisites

You need:

- `zypper`
- `curl`
- `ca-certificates`

## Channels

Emby publishes two RPM channels:

- `stable` (repo alias in the helper script: `Emby`)
- `beta` (repo alias in the helper script: `EmbyBeta`)

You should configure **exactly one** of them.

---

## Stable channel

### 1) Install the repository file

Download the repo definition to:

- `/etc/zypp/repos.d/emby.repo`

```bash
sudo curl -fsSL https://pkg.emby.media/rpm/emby.repo -o /etc/zypp/repos.d/emby.repo
```

### 2) Refresh repositories and import keys

```bash
sudo zypper -n --gpg-auto-import-keys ref
```

---

## Beta channel

### 1) Install the repository file

Download the repo definition to:

- `/etc/zypp/repos.d/emby-beta.repo`

```bash
sudo curl -fsSL https://pkg.emby.media/rpm/emby-beta.repo -o /etc/zypp/repos.d/emby-beta.repo
```

### 2) Refresh repositories and import keys

```bash
sudo zypper -n --gpg-auto-import-keys ref
```

---

## Verify repository configuration

List repositories:

```bash
zypper lr -u
```

Search for packages:

```bash
zypper se -s emby
```

Show package info:

```bash
zypper info emby-server
```

Show available versions (repo-specific search output):

```bash
zypper se -s emby-server
```

---

## Install / upgrade / uninstall examples

Install server:

```bash
sudo zypper -n in emby-server
```

Upgrade system packages:

```bash
sudo zypper -n up
```

Uninstall:

```bash
sudo zypper -n rm emby-server
```

---

## Notes about AppStream / Software Center integration

The Zypper helper script used by `get.sh` installs additional packages to improve AppStream and Software Center integration on openSUSE (e.g., `PackageKit`, AppStream cache tools) and refreshes caches.

For a minimal manual repo setup, the steps in this document are enough to install packages via `zypper`. If you want Software Center/Discover integration, you may also need to install AppStream/PackageKit components and refresh caches (distribution-specific).

---

## Remove the repository

Stable:

```bash
sudo rm -f /etc/zypp/repos.d/emby.repo
sudo zypper -n --gpg-auto-import-keys ref || true
```

Beta:

```bash
sudo rm -f /etc/zypp/repos.d/emby-beta.repo
sudo zypper -n --gpg-auto-import-keys ref || true
```
