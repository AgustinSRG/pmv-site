---
title: Installation on Windows
description: >
  Guide on how to install PersonalMediaVault on a Windows system
categories: [Guides, Installation]
tags: [guides, installation, windows]
---

This guide explains how to download and install PersonalMediaVault on a Windows system.

## Download

Download the [MSI installation package](https://github.com/AgustinSRG/PersonalMediaVault#windows) from any of the available mirrors.

The file should have a name formatted similar to `PersonalMediaVault-A.B.C-x64.msi`, replacing `A`, `B` and `C` for the major, minor and patch version number respectively.

Make sure to check the file hash with **Powershell** and compare it to the provided hash on GitHub.

```ps1
Get-FileHash -Path "PersonalMediaVault-A.B.C-x64.msi" -Algorithm SHA256
```

The hash should perfectly match with the provided one. It is doesn't, do not continue the installation process, and make an [Issue](https://github.com/AgustinSRG/PersonalMediaVault/issues) to report the problem.

## Installing

Once downloaded, run the installer and follow the steps.

The installer should take care of everything for you, installing all the dependencies and placing the binaries in the **Program Files** folder.

## Creating and running a vault

The installer will add an option to the file explorer to open a folder with PersonalMediaVault.

Create a new folder, and use that option to open with PersonalMediaVault.

![Open with PersonalMediaVault](/images/en/windows-open-with.jpg)

That will open the launcher, asking you for an initial username and password for your vault.

After the vault is created, it will ask you for a port to run the server, and will start it, opening your default browser.
