# My personal Nod build

This fork builds its own unsigned Nod desktop installers for **Linux x64** (Flatpak: Ubuntu Desktop, Fedora, Mint, …) and **Windows x64** with GitHub Actions. It uses GitHub's free hosted runners, and it does not use n8n's signing keys, telemetry token or update channel.

## Build

1. In this repository, open **Actions** and enable workflows if GitHub asks.
2. Choose **My build (Linux + Windows)**, then **Run workflow**.
3. When it finishes, about 1–2 hours on free runners, the installers appear under **Releases** and as run artifacts.

## Install

**Windows 11:** run `nod-Setup-x64.exe`. The build is unsigned, so SmartScreen will warn: choose *More info → Run anyway*.

**Ubuntu / Linux:**

```bash
sudo apt install flatpak
cat nod-linux-x64.flatpak.part* > nod-linux-x64.flatpak
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install --user nod-linux-x64.flatpak
flatpak run io.n8n.Nod
```

## Stay up to date

On GitHub, click **Sync fork** on the repository page, then run the workflow again. Builds do not update themselves.

## Upstream workflows

n8n's own workflows (`ci.yml`, `docs.yml`, `security.yml`, `self-host-bundle.yml`, `desktop-release.yml`, …) expect paid "Blacksmith" runners and n8n's secrets. In **Actions**, disable each of them so they do not queue on every sync.
