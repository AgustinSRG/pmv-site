---
title: Overview
description: What is PersonalMediaVault?
weight: 1
---

PersonalMediaVault is an open source tool you can use to create an encrypted, easy to backup and easy to access media gallery.

PersonalMediaVault is a solution to store your personal media files in a secure way, while being able to easily access them from a web browser.

## What do I want it for?

You can use PersonalMediaVault to store and organize your media files, being able to securely backup them in the cloud, thanks to them being encrypted.

You can run the server in local, or in a remote server. 

If you run it in a server, you can access it from multiple devices, only requiring a modern web browser.

## Features

PersonalMediaVault has many useful features. Here is a list of them.

### Encrypted storage

Your media files are encrypted with your password.

PersonalMediaVault uses the AES encryption algorithm, with a key length of 256 bits.

Only you, and who you allow, can access the vault.
Use a strong password, combined with a password manager for more security.

### Easy to backup

The vault is stored in a folder, and always in a consistent status. 

You can easily make a backup of the vault by making a copy of the folder.

You can safely store your vault in any cloud service
without worrying your files being accessed, since they are encrypted.


### Access your vault with a web browser

PersonalMediaVault is implemented as a web application. You can run the server in local, 
or in a security-hardened server depending on your needs.

You can access the vault from any modern web browser, 
using the user-friendly and feature-rich web interface it provides.

### Support for videos, audios and pictures

You can upload videos, audios or pictures to the vault.

They are automatically classified, given a thumbnail if possible, and encoded for the playback in the browser.

Each kind of media has its own player interface, with both generic and specific features.

### Classify your media files with tags

You can give each media file a title, description and classify it with tags.

You can then make searches using those parameters to easily find your media files.

### Use albums to create media lists

You can create ordered lists of media files by creating albums.

Albums are the perfect way to easily accessing your favorite media files,
or keeping a list of media files in order. 

For example a series, a music playlist
or a collection of photos of a particular event.

### Video player features

The web video player the tool provides has many features, including
timeline previews, support for subtitles, support for multiple audio tracks,
support for multiple resolutions and event timeline slices.

The audio player also has many of these features, including a sound
wave animation to fill the blank space.

### Image viewer features

The web image viewer has also many features, including
scaling, multiple resolutions and image annotations.

With image annotations, you can add a text that appears on hovering
or clicking a zone of the image. It's very useful for translations or
any extra information to add to the image.

### Attachments

You can attach any file to a media file. 

The attachment will also be encrypted with the same level of security and stored into the media vault, within the media file.

This can be very useful to store related documents, or original media files you don't want to be encoded, but stored raw.

### Fast and performant

PersonalMediaVault is made to be fast and performant.

The server and main tools are built with the **Go** programming language. 
The web interface has very small bundle sizes.
Multiple caches are in place to further reduce latency.

### Docker

PersonalMediaVault provides a Docker image, so you can easily run a server in the cloud without worrying about dependencies or installations.

You can find the images both on [Docker Hub](https://hub.docker.com/r/asanrom/pmv) and in [GitHub Packages](https://github.com/AgustinSRG/PersonalMediaVault/pkgs/container/personalmediavault).

### Console client

PersonalMediaVault provides a command line interface client for PersonalMediaVault,
so you can access your vault even from a terminal.

This CLI tool can be also used to make automated scripts, in case you need them for advanced tasks.

## What is it not for?

PersonalMediaVault is not an end-to-end encryption storage service. 
The server is meant to be run by the owner of the media files, either in local or into a personal server.

## Where should I go next?

* [Getting Started]({{< baseurl >}}docs/getting-started/): Download, install and run PersonalMediaVault
* [Tutorials]({{< baseurl >}}docs/tutorials/): Check out some guides and tutorials on how to use PersonalMediaVault.

