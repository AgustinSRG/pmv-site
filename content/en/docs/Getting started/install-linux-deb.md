---
title: Installation on Linux
description: >
  Guide on how to install PersonalMediaVault on a Linux system with a deb package
categories: [Guides, Installation]
tags: [guides, installation, linux]
---

This guide explains how to download and install PersonalMediaVault on a Linux system, using the provided DEB package.

You can do it via 2 methods:

 - The GitHub sites PPA repository (provides automatic updates)
 - Manually download and installing the DEB package.

## Install via the PPA repository

Run the following commands to install PersonalMediaVault from the PPA:

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

## Manual download and installation

First, download the [pre-compiled DEB package](https://github.com/AgustinSRG/PersonalMediaVault#linux-with-deb-package-support) from any of the available mirrors.

The file should have a name formatted similar to `personalmediavault_A.B-C.deb`, replacing `A`, `B` and `C` for the major, minor and patch version number respectively.

Make sure to check the file hash with the `sha256sum` utility and compare it to the provided hash on GitHub.

```sh
sha256sum ./personalmediavault_A.B-C.deb
```

The hash should perfectly match with the provided one. It is doesn't, do not continue the installation process, and make an [Issue](https://github.com/AgustinSRG/PersonalMediaVault/issues) to report the problem.

Once downloaded, you can install the DEB package into your system with `apt`:

```sh
sudo apt install ./personalmediavault_A.B-C.deb
```

The installation will also install [FFmpeg](https://ffmpeg.org/) as a dependency.

After the installation, the binary files will be available in `/usr/bin`, and the frontend files will be available in `/usr/lib/pmv/www`.

## Creating and running a vault

In order to create, or open a vault, run the launcher command:

```sh
pmv ./my_vault
```

This command will create a new vault on that folder, asking you for the initial username and password.

After it's created, it will ask you for the port to run the server, and will start it, opening your default browser.
