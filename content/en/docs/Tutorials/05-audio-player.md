---
title: Audio player
description: >
  Learn how to use the audio player, used to play any audio files you store in the vault.
categories: [Tutorials]
tags: [tutorials]
weight: 5
---

When selecting an **audio** in the media vault, the **audio player** will be used in order to play it.

The PersonalMediaVault video player is very similar to the video player, adapted for audio files:

 - At the top-left, you have the audio title
 - At the top-right, you have a button to open the audio metadata editor.
 - At the bottom you have the player controls, and on top of them, you have the timeline. 

![Screenshot]({{< baseurl >}}images/en/audio-player.jpg)

## Basic controls

In order to play or pause, you can simply click the player at the center, use the play button in the player controls bar, or using a keyboard shortcut: **Space Bar** or **K**.

![Screenshot]({{< baseurl >}}images/en/audio-player-play.jpg)

In order to change the volume, you can use the volume control in the player controls bar, which displays a slider when hovering it or clicking it. You can also use a keyboard shortcut, being the **Up** and **Down** arrow keys, which will change the volume by 5%. You can press **Shift** while using the vertical arrow keys in order to fine-tune the volume by changing it 1% each key press.

You can mute or un-mute the audio by clicking on the volume control in the player controls bar, or using the key **M**.

![Screenshot]({{< baseurl >}}images/en/audio-player-volume.jpg)

By pressing the configuration button or the **S** key, you can open the [audio player configuration](#configuration).

![Screenshot]({{< baseurl >}}images/en/audio-player-config-btn.jpg)

By pressing the full screen button, or the **F** key, you can toggle the full screen mode for the audio player.

![Screenshot]({{< baseurl >}}images/en/audio-player-full-screen.jpg)

## Timeline

You can hover the timeline in order to get the timestamp you are hovering into.

![Screenshot]({{< baseurl >}}images/en/audio-player-timeline.jpg)

You can click the timeline in order to change the current time.

You can use the **Home** key to go to the beginning of the audio. Also, you can use the **End** key to go to the end of the audio.

You can also use the **Left** and **Right** arrow keys to go backward or forward by 5 seconds respectively.

Also, if the player is paused, you can use the **dot** and **comma** keys to go backward or forward by a single frame respectively.

## Configuration

You can open the player configuration by pressing the configuration button or the **S** key.

![Screenshot]({{< baseurl >}}images/en/audio-player-config.jpg)

You can find several options:

 - You can toggle the loop option. If enabled, the player will automatically replay the audio from the beginning after it ending. You can press the **L** key to do the same.
 - You can toggle the auto-next option. If enabled, the player will attempt to play the next media in the list after the current audio finishes playing.
 - You can change the playback speed, to accelerate it or slow it down.
 - You can change the animation style used to represent the audio wave.

## Context menu

When right clicking with a mouse, or with a long tap in touch devices, it will open the player context menu, with several options for fast access to them.

![Screenshot]({{< baseurl >}}images/en/audio-player-context-menu.jpg)

You can find several options:

 - You can toggle the loop option. If enabled, the player will automatically replay the video from the beginning after it ending. You can press the **L** key to do the same.
 - You can open the tags editor. You can also press the **T** key to open it.
 - You can open the time slices editor. You can also press the **N** key to open it.
 - You can open the extended description, being an arbitrary text to attach to the media. You can also press the **I** key to open it.
 - You can download the audio file.
 - You can check the size of the files stored in the vault.
 - You can refresh the media, reloading it from the server.

## Editor

You can open the player editor by clicking the expand button at the top right corner of the player. Also you can press the **E** key.

![Screenshot]({{< baseurl >}}images/en/audio-player-editor.jpg)

The player editor allows you to change any aspect of the audio.

In the **General** tab you can change the title of the audio, its description and thumbnail. You can also enable extra flags, like resetting the time when loading the audio every time, instead of restoring the previous time.

In the **Tags** tab you can change the media tags. You can use the tags to find the media later when searching for it.

You also have other tabs we explain in detail in the sections below.

### Subtitles

You can add subtitles to the audio in the **Subtitles** tab of the player editor. You can add them by uploading SubRip files, with `.srt` extension.

When an audio has subtitles, you can select them at the player configuration menu, while also being able to customize their style.

![Screenshot]({{< baseurl >}}images/en/audio-player-subtitles.jpg)

### Time slices

You can split the audio in different slices by clicking the option in the context menu, or pressing the **N** key. This will open an editor where you can add time slices, specifying the start time, and a name.

![Screenshot]({{< baseurl >}}images/en/audio-player-time-slices.jpg)

You can also change the time slices in text mode by going to the  **Time slices** tab of the player editor.

### Attachments

You can add attachments to the audio by going to the **Attachments** tab of the player editor.

Attachments are arbitrary files you can store in the vault along with the media file, for example the original uncompressed audio or the assets used to make it.

### Danger zone

In the **Danger zone** tab of the player editor, you can:

 - Re-encode the audio, in order to attempt to fix encoding errors.
 - Delete the audio from the vault, which requires confirmation. You can also use the **Delete** key.
