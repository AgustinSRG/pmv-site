---
title: Compile from source code
description: >
  Guide on how to compile PersonalMediaVault from source code
categories: [Guides, Installation]
tags: [guides, installation]
---

This guide explains how to compile PersonalMediaVault from source code.

## Requirements

You will need the following tools installed on your system to compile PersonalMediaVault:

 - [Git](https://git-scm.com/downloads)
 - [Golang](https://go.dev/), latest stable version
 - [NodeJS](https://nodejs.org/en), latest stable version

## Install FFMpeg (Dependency)

PersonalMediaVault uses FFmpeg as a dependency to encode media, generate thumbnails among other things.

Download it from the [official website](https://ffmpeg.org/) and install it into your system.

Make sure the `ffmpeg` and `ffprobe` binaries are located inside `/usr/bin`. If they are not, please, set up the following environment variables in your system:

| Variable Name | Description |
|---|---|
| FFMPEG_PATH | Path to `ffmpeg` binary |
| FFPROBE_PATH | Path to `ffprobe` binary |

## Clone repository

Clone the PersonalMediaVault repository with the following command:

```sh
git clone https://github.com/AgustinSRG/PersonalMediaVault
cd PersonalMediaVault
```

## Compile backend

Navigate to the `backend` folder and run the compilation script:

```sh
cd backend
./build-production.sh
cd ..
```

The result will be a binary named `pmvd`. Copy it into `/usr/bin`

## Compile backup tool

Navigate to the `backup-tool` folder and run the compilation script:

```sh
cd backup-tool
./build-production.sh
cd ..
```

The result will be a binary named `pmv-backup`. Copy it into `/usr/bin`

## Compile launcher

Navigate to the `launcher` folder and run the compilation script:

```sh
cd launcher
./build-production.sh
cd ..
```

The result will be a binary named `pmv`. Copy it into `/usr/bin`

## Compile frontend

Navigate to the `frontend` folder and run the compilation script:

```sh
cd frontend
npm install
npm run build
cd ..
```

The result will be a folder named `dist`. Copy its contents into `/usr/lib/pmv/www`

If you prefer to store the frontend into another path, make sure to set the following environment variable in your system:

| Variable Name | Description |
|---|---|
| FRONTEND_PATH | Path to static frontend to serve it. |

## Creating and running a vault

In order to create, or open a vault, run the launcher command:

```sh
pmv ./my_vault
```

This command will create a new vault on that folder, asking you for the initial username and password.

After it's created, it will ask you for the port to run the server, and will start it, opening your default browser.
