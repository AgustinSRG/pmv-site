---
title: Video player
description: >
  Learn how to use the video player, used to play any video files you store in the vault.
categories: [Tutorials]
tags: [tutorials]
weight: 3
---

When selecting a **video** in the media vault, the **video player** will be used in order to play it.

The PersonalMediaVault video player is a feature rich player based on the YouTube video player:

 - At the top-left, you have the video title
 - At the top-right, you have a button to open the video metadata editor.
 - At the bottom you have the player controls, and on top of them, you have the timeline. 

![Screenshot]({{< baseurl >}}images/en/video-player.jpg)

## Basic controls

In order to play or pause, you can simply click the player at the center, use the play button in the player controls bar, or using a keyboard shortcut: **Space Bar** or **K**.

![Screenshot]({{< baseurl >}}images/en/video-player-play.jpg)

In order to change the volume, you can use the volume control in the player controls bar, which displays a slider when hovering it or clicking it. You can also use a keyboard shortcut, being the **Up** and **Down** arrow keys, which will change the volume by 5%. You can press **Shift** while using the vertical arrow keys in order to fine-tune the volume by changing it 1% each key press.

You can mute or un-mute the video by clicking on the volume control in the player controls bar, or using the key **M**.

![Screenshot]({{< baseurl >}}images/en/video-player-volume.jpg)

By pressing the configuration button or the **S** key, you can open the [video player configuration](#configuration).

![Screenshot]({{< baseurl >}}images/en/video-player-config-btn.jpg)

By pressing the full screen button, or the **F** key, you can toggle the full screen mode for the video player.

![Screenshot]({{< baseurl >}}images/en/video-player-full-screen.jpg)

## Timeline

You can hover the timeline in order to get the timestamp you are hovering into, and an image preview, if available.

![Screenshot]({{< baseurl >}}images/en/video-player-timeline.jpg)

You can click the timeline in order to change the current time.

You can use the **Home** key to go to the beginning of the video. Also, you can use the **End** key to go to the end of the video.

You can also use the **Left** and **Right** arrow keys to go backward or forward by 5 seconds respectively.

Also, if the player is paused, you can use the **dot** and **comma** keys to go backward or forward by a single frame respectively.

## Configuration

You can open the player configuration by pressing the configuration button or the **S** key.

![Screenshot]({{< baseurl >}}images/en/video-player-config.jpg)

You can find several options:

 - You can toggle the loop option. If enabled, the player will automatically replay the video from the beginning after it ending. You can press the **L** key to do the same.
 - You can toggle the auto-next option. If enabled, the player will attempt to play the next media in the list after the current video finishes playing.
 - You can change the playback speed, to accelerate it or slow it down.
 - You can change the scale of the video, in order to zoom-in to check small details.
 - You can change the video quality (resolution and frames per seconds) between the available ones.
 - You can also change the subtitles, and the audio track, if they are available for your video.
 - You can also change the toggle play delay, being the play/pause delay when you click the player at its center.

## Context menu

When right clicking with a mouse, or with a long tap in touch devices, it will open the player context menu, with several options for fast access to them.

![Screenshot]({{< baseurl >}}images/en/video-player-context-menu.jpg)

You can find several options:

 - You can toggle the loop option. If enabled, the player will automatically replay the video from the beginning after it ending. You can press the **L** key to do the same.
 - You can hide or show the controls. When done with this options, the controls will stay hidden until you disable the option. You can press the **C** key to do the same.
 - You can open the tags editor. You can also press the **T** key to open it.
 - You can open the time slices editor. You can also press the **N** key to open it.
 - You can open the extended description, being an arbitrary text to attach to the media. You can also press the **I** key to open it.
 - You can download the video file.
 - You can check the size of the files stored in the vault.
 - You can refresh the media, reloading it from the server.

## Editor

You can open the player editor by clicking the expand button at the top right corner of the player. Also you can press the **E** key.

![Screenshot]({{< baseurl >}}images/en/video-player-editor.jpg)

The player editor allows you to change any aspect of the video.

In the **General** tab you can change the title of the video, its description and thumbnail. You can also enable extra flags, like resetting the time when loading the video every time, instead of restoring the previous time.

In the **Tags** tab you can change the media tags. You can use the tags to find the media later when searching for it.

You also have other tabs we explain in detail in the sections below.

### Subtitles

You can add subtitles to the video in the **Subtitles** tab of the player editor. You can add them by uploading SubRip files, with `.srt` extension.

If you upload a Matroska file (`.mkv` extension) to the vault, the available subtitles will be automatically extracted.

When a video has subtitles, you can select them at the player configuration menu, while also being able to customize their style.

![Screenshot]({{< baseurl >}}images/en/video-player-subtitles.jpg)

### Audio tracks

You can add extra audio tracks for the video in the **Audio Tracks** tab of the player editor. You can add them by uploading audio files, for example with `.mp3` extension.

If you upload a Matroska file (`.mkv` extension) to the vault, the available audio tracks will be automatically extracted.

When a video has extra audio tracks, you can select the one that will play at the player configuration menu.

![Screenshot]({{< baseurl >}}images/en/video-player-audios.jpg)

### Time slices

You can split the video in different slices by clicking the option in the context menu, or pressing the **N** key. This will open an editor where you can add time slices, specifying the start time, and a name.

![Screenshot]({{< baseurl >}}images/en/video-player-time-slices.jpg)

You can also change the time slices in text mode by going to the  **Time slices** tab of the player editor.

### Attachments

You can add attachments to the video by going to the **Attachments** tab of the player editor.

Attachments are arbitrary files you can store in the vault along with the media file, for example the original uncompressed video or the assets used to make it.

### Resolutions

In the **Resolutions** tab of the player editor, you will be able to resize the video to different resolutions, in order to play it in smaller screens without wasting bandwidth.

Once a resolution is available, you will be able to select it from the player configuration menu.

### Danger zone

In the **Danger zone** tab of the player editor, you can:

 - Re-encode the video, in order to attempt to fix encoding errors.
 - Delete the video from the vault, which requires confirmation. You can also use the **Delete** key.
