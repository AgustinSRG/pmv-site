---
title: PersonalMediaVault
---

{{< blocks/cover title="Welcome to PersonalMediaVault!" image_anchor="top" height="full" >}}
<a class="btn btn-lg btn-primary me-3 mb-4" href="./docs/">
  Learn More <i class="fas fa-arrow-alt-circle-right ms-2"></i>
</a>
<a class="btn btn-lg btn-secondary me-3 mb-4" href="https://github.com/AgustinSRG/PersonalMediaVault/releases">
  Download <i class="fas fa-download ms-2 "></i>
</a>
<p class="lead mt-5">Web application to store media files (video, audio and pictures) in an encrypted storage, and visualize them using a web browser.</p>
{{< blocks/link-down color="info" >}}
{{< /blocks/cover >}}


{{% blocks/lead color="primary" %}}
PersonalMediaVault is an open source tool you can use to create
an encrypted, easy to backup and easy to access media gallery.

PersonalMediaVault is a solution to store your personal media files in a secure way, 
while being able to easily access them from a web browser.
{{% /blocks/lead %}}


{{% blocks/section color="dark" type="row" %}}

{{% blocks/feature icon="fas fa-lock" title="Encrypted storage" %}}
Your media files are encrypted with your password.

PersonalMediaVault uses the AES encryption algorithm, with a key length of 256 bits.

Only you, and who you allow, can access the vault.
Use a strong password, combined with a password manager for more security.
{{% /blocks/feature %}}


{{% blocks/feature icon="fas fa-cloud" title="Easy to backup" %}}
The vault is stored in a folder, and always in a consistent status. 

You can easily make a backup of the vault by making a copy of the folder.

You can safely store your vault in any cloud service
without worrying your files being accessed, since they are encrypted.
{{% /blocks/feature %}}


{{% blocks/feature icon="fab fa-chrome" title="Access your vault with a web browser" %}}
PersonalMediaVault is implemented as a web application. You can run the server in local, 
or in a security-hardened server depending on your needs.

You can access the vault from any modern web browser, 
using the user-friendly and feature-rich web interface it provides.
{{% /blocks/feature %}}


{{% blocks/feature icon="fas fa-photo-film" title="Support for videos, audios and pictures" %}}
You can upload videos, audios or pictures to the vault.

They are automatically classified, given a thumbnail if possible, and encoded for the playback in the browser.

Each kind of media has its own player interface, with both generic and specific features.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-tags" title="Classify your media files with tags" %}}
You can give each media file a title, description and classify it with tags.

You can then make searches using those parameters to easily find your media files.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-list-ol" title="Use albums to create media lists" %}}
You can create ordered lists of media files by creating albums.

Albums are the perfect way to easily accessing your favorite media files,
or keeping a list of media files in order. 

For example a series, a music playlist
or a collection of photos of a particular event.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-video" title="Video player features" %}}
The web video player the tool provides has many features, including
timeline previews, support for subtitles, support for multiple audio tracks,
support for multiple resolutions and event timeline slices.

The audio player also has many of these features, including a sound
wave animation to fill the blank space.
{{% /blocks/feature %}}


{{% blocks/feature icon="fas fa-image" title="Image viewer features" %}}
The web image viewer has also many features, including
scaling, multiple resolutions and image annotations.

With image annotations, you can add a text that appears on hovering
or clicking a zone of the image. It's very useful for translations or
any extra information to add to the image.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-paperclip" title="Attachments" %}}
You can attach any file to a media file. 

The attachment will also be encrypted with the same level of security and stored into the media vault, within the media file.

This can be very useful to store related documents, or original media files you don't want to be encoded, but stored raw.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-bolt" title="Fast and performant" %}}
PersonalMediaVault is made to be fast and performant.

The server and main tools are built with the **Go** programming language. 
The web interface has very small bundle sizes.
Multiple caches are in place to further reduce latency.
{{% /blocks/feature %}}

{{% blocks/feature icon="fab fa-docker" title="Docker" url="/docs/getting-started/docker/" %}}
PersonalMediaVault provides a Docker image, so you can easily run a server in the cloud without worrying about dependencies or installations.

You can find the images both on [Docker Hub](https://hub.docker.com/r/asanrom/pmv) and in [GitHub Packages](https://github.com/AgustinSRG/PersonalMediaVault/pkgs/container/personalmediavault).
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-terminal" title="Console client" url="/docs/console-client/" %}}
PersonalMediaVault provides a command line interface client for PersonalMediaVault,
so you can access your vault even from a terminal.

This CLI tool can be also used to make automated scripts, in case you need them for advanced tasks.
{{% /blocks/feature %}}

{{% /blocks/section %}}


{{% blocks/section %}}
PersonalMediaVault is a free and open source project
{.h1 .text-center}
{{% /blocks/section %}}


{{% blocks/section type="row" %}}

{{% blocks/feature icon="fas fa-scale-balanced" title="MIT License" %}}
The project is under the [MIT License](https://github.com/AgustinSRG/PersonalMediaVault/blob/master/LICENSE).

You can freely distribute the project, make any changes or even use for commercial purposes
{{% /blocks/feature %}}

{{% blocks/feature icon="fab fa-github" title="Contributions welcome!"
    url="https://github.com/google/docsy-example" %}}
Fell free to make a [Pull Request](https://github.com/AgustinSRG/PersonalMediaVault/pulls)
on **GitHub** for any feature or bug fix you want to contribute to the project.
{{% /blocks/feature %}}

{{% blocks/feature icon="fas fa-comment-dots" title="Questions or issues?" %}}
Any question of issues can be handled on **GitHub**.

If you have any question, feel free to open a [Discussion](https://github.com/AgustinSRG/PersonalMediaVault/discussions).

If you find a bug, and you want to report it, please open an [Issue](https://github.com/AgustinSRG/PersonalMediaVault/issues).
{{% /blocks/feature %}}

{{% /blocks/section %}}
