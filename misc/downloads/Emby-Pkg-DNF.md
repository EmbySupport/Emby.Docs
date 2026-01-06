---
uid: Emby-Pkg-DNF
title: Manual Repo Setup: DNF
---

# Manual setup: DNF 

## Fedora / RHEL / CentOS

This guide explains how to configure the Emby RPM repository manually for DNF-based systems (without using `get.sh`).

## Prerequisites

You need:

- `dnf`
- `curl`
- `ca-certificates`

On some distributions, `dnf config-manager` is provided by `dnf-plugins-core`.

## Channels

Emby publishes two RPM channels:

- `stable` (repo id: `emby`)
- `beta` (repo id: `emby-beta`)

You should configure **exactly one** of them.

---

## Option A (simple): use `dnf config-manager` with the published `.repo`

This matches the short form shown on the website.

### Stable

```bash
sudo dnf config-manager --add-repo https://pkg.emby.media/rpm/emby.repo
sudo dnf makecache
```

### Beta

```bash
sudo dnf config-manager --add-repo https://pkg.emby.media/rpm/emby-beta.repo
sudo dnf makecache
```

Notes:
- The `.repo` file is installed under `/etc/yum.repos.d/`.
- DNF may prompt to import a GPG key the first time it uses the repo.

---

## Option B (recommended for non-interactive/manual control): download the `.repo` and import the key proactively

This mirrors the behavior of `tree_update/rpm/setup-dnf.sh` (used by `get.sh`).

### Stable

1) Download the repo file:

```bash
sudo curl -fsSL https://pkg.emby.media/rpm/emby.repo -o /etc/yum.repos.d/emby.repo
```

2) Download and import the signing key:

- Key URL: `https://pkg.emby.media/keys/emby-public.asc`
- Local key path (recommended): `/etc/pki/rpm-gpg/emby-public.asc`

```bash
sudo install -d -m 0755 /etc/pki/rpm-gpg
sudo curl -fsSL https://pkg.emby.media/keys/emby-public.asc -o /etc/pki/rpm-gpg/emby-public.asc
sudo rpm --import /etc/pki/rpm-gpg/emby-public.asc 2>/dev/null || sudo rpmkeys --import /etc/pki/rpm-gpg/emby-public.asc || true
```

3) Ensure the repo file uses the local `file://` key path (prevents repeated prompts):

```bash
sudo sed -i -E 's|^[[:space:]]*gpgkey=.*$|gpgkey=file:///etc/pki/rpm-gpg/emby-public.asc|' /etc/yum.repos.d/emby.repo
```

4) Refresh metadata:

```bash
sudo dnf -y clean metadata || true
sudo dnf -y makecache --refresh --repo emby
```

### Beta

Same steps, but using the beta `.repo` file and repo id:

```bash
sudo curl -fsSL https://pkg.emby.media/rpm/emby-beta.repo -o /etc/yum.repos.d/emby-beta.repo

sudo install -d -m 0755 /etc/pki/rpm-gpg
sudo curl -fsSL https://pkg.emby.media/keys/emby-public.asc -o /etc/pki/rpm-gpg/emby-public.asc
sudo rpm --import /etc/pki/rpm-gpg/emby-public.asc 2>/dev/null || sudo rpmkeys --import /etc/pki/rpm-gpg/emby-public.asc || true

sudo sed -i -E 's|^[[:space:]]*gpgkey=.*$|gpgkey=file:///etc/pki/rpm-gpg/emby-public.asc|' /etc/yum.repos.d/emby-beta.repo

sudo dnf -y clean metadata || true
sudo dnf -y makecache --refresh --repo emby-beta
```

---

## Verify repository configuration

List known repos and confirm `emby` or `emby-beta` is present:

```bash
dnf repolist --all | grep -E '^(emby|emby-beta)'
```

Show package info:

```bash
dnf info emby-server
```

List available packages (basic search):

```bash
dnf search emby
```

List available versions (shows duplicates):

```bash
dnf list --showduplicates emby-server
```

---

## Install / upgrade / uninstall examples

Install server:

```bash
sudo dnf install emby-server
```

Upgrade:

```bash
sudo dnf upgrade
```

Uninstall:

```bash
sudo dnf remove emby-server
```

---

## Remove the repository

Stable:

```bash
sudo rm -f /etc/yum.repos.d/emby.repo
sudo dnf -y clean metadata || true
```

Beta:

```bash
sudo rm -f /etc/yum.repos.d/emby-beta.repo
sudo dnf -y clean metadata || true
```

(You can keep `/etc/pki/rpm-gpg/emby-public.asc` if you plan to re-add the repo later.)
