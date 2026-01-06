---
uid: Emby-Pkg-Installer
title: Emby Universal Installer
---

# Emby Universal installer

## As Easy as it can be!


<div class="universal-installer">
    <div class="codewrapper" style="line-height: 1.5;"><pre class="rp-pre"><code class="lang-bash hljs" style="font-weight: 600;   color: #7d7d7d;">curl https://pkg.emby.media/get.sh | sh</code></pre><button type="button" class="copy-btn" aria-label="Copy to clipboard"><i class="fa fa-clipboard" aria-hidden="true"></i><span class="copy-label">Copy</span></button><div class="copy-toast" role="status" aria-live="polite">Copied to clipboard</div></div>
    <div class="rp-description">Use the button to copy-paste or type the command to run in a terminal</div>
</div>

<p style="text-align: center;font-weight: 500;color: #6f6f6f;">All apps - all distros - all architectures <br/> all channels - all package managers - all versions  <br/>ONE COMMAND
    </p>

### About

`get.sh` is the recommended way to set up the Emby package repository on Linux. It is a single, universal script that:

- detects your system’s package manager automatically (APT, DNF, Zypper, Pacman)
- guides you through repository setup and package installation
- avoids immediate elevation: it runs as a regular user and only requests root permissions for actions that require it


---

## Quick start (interactive)

- Run the installer script as shown above.
- Then follow the prompts:

1. Choose channel (`stable` or `beta`)
2. Register/unregister repository (or show packages if already registered)
3. Choose an app/package
4. Install/uninstall/view info (and optionally open Software Center if supported)

---

## Non-interactive usage (automation)

`get.sh` supports non-interactive usage via environment variables.

### Environment variables

- `ch` = `stable|beta`  
  Selects repository channel.

- `rop` = `R|S|U`  
  Repository operation:
  - `R` = register (or “reload” if already registered)
  - `S` = show packages (requires repo already registered)
  - `U` = unregister (requires repo already registered)

- `app` = package id (required when `rop=S`)  
  Examples: `emby-server`, `media.emby.client`, `media.emby.client.beta`

- `aop` = operation when `rop=S` (required when `rop=S`)  
  Valid operations depend on app state and platform (the script will reject invalid combinations):
  - `I` = install (latest)
  - `U` = uninstall
  - `V` = choose a specific version (only offered when multiple versions exist)
  - `S` = show app info
  - `K` = block/unblock package from auto-updating (not available on Pacman)

- `GET_LOCAL` = `1`  
  Local test mode. Instead of downloading platform helper scripts from `pkg.emby.media`, the script will use local files from `./tree_update/` (useful when developing this repository).

### Examples

Register stable repo:

```sh
curl -fsSL https://pkg.emby.media/get.sh | env ch=stable rop=R sh
```

Unregister beta repo:

```sh
curl -fsSL https://pkg.emby.media/get.sh | env ch=beta rop=U sh
```

Show packages (beta) and install the beta client:

```sh
curl -fsSL https://pkg.emby.media/get.sh | env ch=beta rop=S app=media.emby.client.beta aop=I sh
```

---

## What `get.sh` does (high level)

### 1) Detects the platform (package manager)

`get.sh` selects the first supported platform it finds:

- APT if `apt-get` is available
- Pacman if `pacman` is available
- DNF if `dnf` is available
- Zypper if `zypper` is available

If `rpm-ostree` is detected, `get.sh` prints a message with manual steps and exits (rpm-ostree is not currently supported by the interactive installer).

If none of the above is found, the script exits with an error.

### 2) Fetches a platform helper script

After detecting the platform, `get.sh` fetches exactly one helper script (unless `GET_LOCAL=1` is used):

- APT: `https://pkg.emby.media/apt/setup.sh`
- Pacman: `https://pkg.emby.media/pac/setup.sh`
- DNF: `https://pkg.emby.media/rpm/setup-dnf.sh`
- Zypper: `https://pkg.emby.media/rpm/setup-zypper.sh`

That helper script provides a shared set of functions (an “interface”) that `get.sh` calls to:
- check whether the repository is registered
- register/unregister the repository
- list available packages
- install/uninstall packages, show package info, etc.

### 3) Performs requested actions

Repository-level actions:
- Register (or reload) repository for the chosen channel
- Unregister repository for the chosen channel

App/package actions:
- Install/uninstall
- Show package information
- Select and install a specific version (when supported and multiple versions exist)
- Block/unblock package from auto-updating (APT, DNF, Zypper only)

---

## Cross-channel update protection

When you have both the stable and beta repositories registered, there's a risk of accidentally upgrading your Emby Server from one channel to another during routine system updates. To prevent this, `get.sh` includes automatic cross-channel update protection.

### Automatic blocking

When registering a repository, `get.sh` automatically blocks cross-channel server updates:

- **Registering the beta repo with a stable Emby Server installed**: The script automatically blocks `emby-server` from the beta repo, preventing accidental upgrades to beta versions.

- **Registering the stable repo with a beta Emby Server installed**: The script automatically blocks `emby-server` from the stable repo, preventing accidental downgrades to stable versions.

When automatic blocking occurs, you'll see a message like:

```
An Emby Server (stable) installation was detected on this system.
The Emby Server package from the beta repo has been blocked automatically
in order to prevent automatic updates being offered, which could
lead to unwanted installation of a beta server version over your
stable installation.
```

### Manual blocking/unblocking

You can also manually control package update blocking from the package operations menu:

1. Navigate to the package in the packages list
2. Select the package to view operations
3. Use the **K** option to toggle blocking:
   - If currently blocked: "Unblock package from auto-updating"
   - If not blocked: "Block package from auto-updating"

Blocked packages are shown in the package list with "(updates blocked)" next to their status.

### Platform implementation

The blocking feature uses platform-native mechanisms:

- **APT**: Creates pinning rules in `/etc/apt/preferences.d/` with negative priority
- **DNF**: Adds `excludepkgs=` to the repo file in `/etc/yum.repos.d/`
- **Zypper**: Creates repo-scoped package locks via `zypper addlock -r`
- **Pacman**: Not supported (no beta server packages available)

---

## Security model / elevation

- `get.sh` is designed to be safe to run as a regular user.
- When a privileged action is needed, `get.sh` tries to use an elevation tool:
  - `sudo` (most common)
  - `doas`
  - `run0`
  - `pkexec`
  - `sudo-rs`

If no elevation tool is available and you are not already running as root, operations that require root privileges will fail with an error.

---

## Troubleshooting

### “Could not find a supported package manager”
Your system must have one of: APT, Pacman, DNF, or Zypper.

### “No elevation tool available”
Install `sudo` (or another supported elevation tool) and re-run.

### “This system uses rpm-ostree which is not yet supported”
Follow the instructions printed by `get.sh` (it suggests installing the `.repo` file and using `rpm-ostree install ...`, then rebooting).

### Debugging downloads
`get.sh` uses either `curl` or `wget` (whichever is available). If downloads fail, verify connectivity to `https://pkg.emby.media/`.

---

## Local development / testing (`GET_LOCAL=1`)

From the repository root:

```sh
GET_LOCAL=1 env ch=stable rop=R sh tree_update/get.sh
```

This forces `get.sh` to use `tree_update/apt/setup.sh`, `tree_update/pac/setup.sh`, etc. instead of downloading them.


<style>

.universal-installer {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 20px 0 0px 0;
}

.codewrapper {
    position: relative;
    display: flex;
    margin-top: 20px;
    margin-bottom: 9px;
    width: fit-content;
}

*, :after, :before {
    box-sizing: border-box;
}


pre {
    border: 0;
    padding: 9.5px;
    margin: 20px 0;
    font-size: 15px;
    word-break: break-all;
    word-wrap: break-word;
    background-color: #f8f8f7;
    border-radius: 4px;
    border: none;
    box-shadow: var(--card-box-shadow);
    display: block;
    font-family: monospace;
    unicode-bidi: isolate;
    white-space: pre;
    margin-block: 1em 1em;
    margin-inline: 0px;
}

pre.rp-pre {
    margin-top: 0;
    margin-bottom: 0;
    padding-right: 60px;
    padding-left: 15px;
}

.rp-description {
    font-size: 11px;
    color: #9f9f9f;
    margin-bottom: 20px;
}

h1#emby-package-repositories {
    margin-left: 200px;
    color: white;
    margin-top: 25px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: clip;
    font-size: 36px;
}

h3#rp-single-commandD {
    font-weight: 400;
    margin-bottom: 0px;
    margin-top: 20px;
    margin-right: 22px;
}

ul.rp-list {
    list-style: none;
    padding-inline-start: 0; margin-right: 30px;
    user-select: none;
}


.copy-btn {
    position: absolute;
    top: 0;
    bottom: 1px;
    right: 0;
    z-index: 10;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 10px;
    font-size: 12px;
    line-height: 1;
    color: var(--font-color);
    background: #fff;
    border: 1px solid #ddd;
    border-radius: 6px;
    box-shadow: var(--card-box-shadow);
    transition: transform 120ms ease, box-shadow var(--transition), color var(--transition), border-color var(--transition);
    margin: 3px;
    opacity: 0.6;
}

.copy-btn .fa {
    font-size: 14px;
}

.copy-btn:hover, .copy-btn:focus {
    color: var(--highlight-dark);
    border-color: var(--highlight-light);
    outline: none;
    /* transform: translateY(-1px); */
}

.copy-btn.is-copied {
    color: #2e7d32;
    border-color: #2e7d32;
}

.copy-btn.is-error {
    color: #c62828;
    border-color: #c62828;
}

.copy-toast {
    position: absolute;
    top: -36px;
    right: 8px;
    background: #212121;
    color: #fff;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 12px;
    box-shadow: var(--card-box-shadow);
    opacity: 0;
    transform: translateY(-6px);
    pointer-events: none;
    transition: opacity 150ms ease, transform 150ms ease;
}

.copy-toast.show {
    opacity: 1;
    transform: translateY(0);
}

/* Respect small screens: keep button tappable */
@media (max-width: 480px) {
    .copy-btn {
        padding: 8px 12px;
        font-size: 13px;
    }
}

.copy-label {
    display: none;
}

</style>

<script>
(function() {
  function makeWrapper(pre) {
    if (pre.parentElement && pre.parentElement.classList.contains('codewrapper')) return pre.parentElement;
    const wrap = document.createElement('div');
    wrap.className = 'codewrapper';
    pre.parentNode.insertBefore(wrap, pre);
    wrap.appendChild(pre);
    return wrap;
  }

  function createButton() {
    const btn = document.createElement('button');
    btn.type = 'button';
    btn.className = 'copy-btn';
    btn.setAttribute('aria-label', 'Copy to clipboard');
    btn.innerHTML = '<i class="fa fa-clipboard" aria-hidden="true"></i><span class="copy-label">Copy</span>';
    return btn;
  }

  function createToast() {
    const div = document.createElement('div');
    div.className = 'copy-toast';
    div.setAttribute('role', 'status');
    div.setAttribute('aria-live', 'polite');
    div.textContent = 'Copied to clipboard';
    return div;
  }

  function getCodeText(codeEl) {
    return (codeEl.innerText || codeEl.textContent || '').trim();
  }

  function fallbackCopy(text) {
    const ta = document.createElement('textarea');
    ta.value = text;
    ta.style.position = 'fixed';
    ta.style.top = '-1000px';
    ta.style.left = '-1000px';
    document.body.appendChild(ta);
    ta.select();
    ta.setSelectionRange(0, text.length);
    let ok = false;
    try { ok = document.execCommand('copy'); } catch (_) { ok = false; }
    document.body.removeChild(ta);
    return ok;
  }

  function setState(btn, toast, state) {
    const label = btn.querySelector('.copy-label');
    const icon = btn.querySelector('.fa');
    btn.classList.remove('is-copied', 'is-error');
    toast.classList.remove('show');
    if (state === 'copied') {
      btn.classList.add('is-copied');
      if (icon) icon.className = 'fa fa-check';
      if (label) label.textContent = 'Copied!';
      toast.textContent = 'Copied to clipboard';
      toast.classList.add('show');
    } else if (state === 'error') {
      btn.classList.add('is-error');
      if (icon) icon.className = 'fa fa-times';
      if (label) label.textContent = 'Copy failed';
      toast.textContent = 'Copy failed';
      toast.classList.add('show');
    } else {
      if (icon) icon.className = 'fa fa-clipboard';
      if (label) label.textContent = 'Copy';
    }
  }

  function attach(pre) {
    const wrap = makeWrapper(pre);
    const code = pre.querySelector('code') || pre;
    const btn = createButton();
    const toast = createToast();
    wrap.appendChild(btn);
    wrap.appendChild(toast);

    let resetTimer = null;
    function reset() {
      setState(btn, toast, 'idle');
      btn.disabled = false;
    }

    btn.addEventListener('click', async function() {
      const text = getCodeText(code);
      if (!text) return;
      btn.disabled = true;
      try {
        if (navigator.clipboard && navigator.clipboard.writeText) {
          await navigator.clipboard.writeText(text);
          setState(btn, toast, 'copied');
        } else {
          const ok = fallbackCopy(text);
          setState(btn, toast, ok ? 'copied' : 'error');
        }
      } catch (e) {
        const ok = fallbackCopy(text);
        setState(btn, toast, ok ? 'copied' : 'error');
      }
      clearTimeout(resetTimer);
      resetTimer = setTimeout(reset, 1800);
    });
  }

  document.addEventListener('DOMContentLoaded', function() {
    document.querySelectorAll('pre').forEach(attach);
  });
})();
</script>
