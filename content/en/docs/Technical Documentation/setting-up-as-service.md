---
title: Setting up as service (systemd)
description: >
  Learn how to set up the PersonalMediaVault server as a systemd service.
categories: [Guides, Tutorials, Technical]
tags: [guides, tutorials, technical, documentation]
---

This technical guide explains how to set up PersonalMediaVault as a service in a Linux machine using systemd.

Make sure to follow the [installation guide on Linux](/docs/getting-started/install-linux-deb/) before doing this. This guide expects you to have PersonalMediaVault already installed in your system.

The first step for creating a systemd service is to create an user for that service.

In order to create the user, run the following commands:

```sh
sudo groupadd pmv
sudo useradd -M pmv -g pmv
sudo usermod -L pmv
```

After you did this, now it's time to create a folder to store the vault. In this guide we are going to use `/var/pmv/vault`.

Run the following commands:

```sh
sudo mkdir /var/pmv
sudo mkdir /var/pmv/vault
sudo chown -R pmv:pmv /var/pmv
```

Then, it's time to create the service file, run the following command:

```sh
sudo nano /etc/systemd/system/pmv.service
```

Copy the following contents and save it:

```conf
[Unit]
Description=PersonalMediaVault
After=network.target auditd.service

[Service]
Type=simple
ExecStart=/usr/bin/pmvd --daemon --log-requests --skip-lock --vault-path /var/pmv/vault
User=pmv
Group=pmv
WorkingDirectory=/var/pmv/vault
Environment=FRONTEND_PATH=/usr/lib/pmv/www
Environment=FFMPEG_PATH=/usr/bin/ffmpeg
Environment=FFPROBE_PATH=/usr/bin/ffprobe
Environment=TEMP_PATH=/tmp/pmv
LimitNOFILE=infinity
LimitCORE=infinity
KillMode=process
StandardInput=null
StandardOutput=syslog
StandardError=syslog
Restart=always

[Install]
WantedBy=multi-user.target
```

Note: You may want to change some options. For that, make sure to check the following:

 - [Server options for PersonalMediaVault](/docs/technical-documentation/server-options/)
 - [Systemd service file manual](https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html)

After you saved the service file, and exited the editor, run the following command to enable the service, so it runs every time the system starts:

```sh
sudo systemctl enable pmv
```

Then, you can start it:

```sh
sudo systemctl start pmv
```

After it was started, you can check the logs with [journalctl](https://man7.org/linux/man-pages/man1/journalctl.1.html). Example:

```sh
sudo journalctl -u pmv
```

You can also check the service status with:

```sh
sudo systemctl status pmv
```
