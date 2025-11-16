---
title: Installation on Linux
description: >
  Guide on how to install PersonalMediaVault on a Linux system with a deb package
categories: [Guides, Installation]
tags: [guides, installation, linux]
---

This guide explains how to download and install PersonalMediaVault on a Linux system, using one of the provided installation packages

Depending on your Linux distribution, we offer several packages.

## Debian, Ubuntu or other Debian based Linux distribution

For Debian-based Linux distributions, download the **DEB** package (`personalmediavault_{VERSION}_amd64.deb`) from [Releases](https://github.com/AgustinSRG/PersonalMediaVault/releases).

Install the package, with `apt` or with your graphical package manager.

You can also install it directly from the PPA repository (built automatically with GitHub actions):

```sh
# Download the public key
curl -s --compressed "https://agustinsrg.github.io/PersonalMediaVault/KEY.gpg" | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/pmv.gpg >/dev/null

# Add the APT list file
sudo curl -s --compressed -o /etc/apt/sources.list.d/pmv.list "https://agustinsrg.github.io/PersonalMediaVault/pmv.list"

# Update APT lists
sudo apt update

# Install the package
sudo apt install personalmediavault
```

After it's installed, you can run the launcher with `pmv /path/to/vault` or the graphical launcher by searching for "PersonalMediaVault" in your application menu.

### Fedora Linux

For Fedora-based Linux distributions, download the **RPM** package (`personalmediavault-{VERSION}.x86_64.rpm`) from [Releases](https://github.com/AgustinSRG/PersonalMediaVault/releases).

Install the package, with `dnf` or with your graphical package manager.

After it's installed, you can run the launcher with `pmv /path/to/vault` or the graphical launcher by searching for "PersonalMediaVault" in your application menu.

### Arch Linux

For Arch-based Linux distributions, download the **PKG.TAR.ZST** package (`personalmediavault-{VERSION}-x86_64.pkg.tar.zst`) from [Releases](https://github.com/AgustinSRG/PersonalMediaVault/releases).

Install the package, with `pacman`:

```sh
sudo pacman -U personalmediavault-{VERSION}-x86_64.pkg.tar.zst
```

After it's installed, you can run the launcher with `pmv /path/to/vault` or the graphical launcher by searching for "PersonalMediaVault" in your application menu.

### Other Linux distribution

For any other Linux distribution, you can download the **TAR.GZ** package (`personalmediavault_{VERSION}_amd64.tar.gz`) from [Releases](https://github.com/AgustinSRG/PersonalMediaVault/releases).

Uncompress it, and run the installation script (`install.sh`) with administration privileges:

```sh
sudo ./install.sh
```

After it's installed, you can run the launcher with `pmv /path/to/vault` or the graphical launcher by searching for "PersonalMediaVault" in your application menu.

### KDE service menu

If you are using a Linux distribution, and KDE as your desktop environment, you can get the same context menu options to open vaults that are installed in the Windows package.

Create the file `~/.local/share/kio/servicemenus/pmv-open.desktop` with the following contents:

```conf
[Desktop Entry]
Name=Open with PersonalMediaVault
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=inode/directory
Actions=openWithPmv

[Desktop Action openWithPmv]
Name=Open with PersonalMediaVault
Name[es]=Abrir con PersonalMediaVault
Terminal=false
Icon=pmv
StartupWMClass=pmv
Exec=pmv-gui .
```

If you prefer to use the console launcher instead, use the following desktop entry:

```conf
[Desktop Entry]
Name=Open with PersonalMediaVault (Console)
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=inode/directory
Actions=openWithPmvConsole

[Desktop Action openWithPmvConsole]
Name=Open with PersonalMediaVault (Console)
Name[es]=Abrir con PersonalMediaVault (Consola)
Terminal=false
Icon=pmv
StartupWMClass=pmv
Exec=konsole --separate -e 'pmv .'
```

