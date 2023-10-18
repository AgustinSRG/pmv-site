---
title: Run with Docker
description: >
  Guide on how to run PersonalMediaVault with Docker
categories: [Guides, Installation, Technical]
tags: [guides, installation, technical, docker]
---

This guide explains how to run PersonalMediaVault with Docker.

## Pull image

First, select a Docker repository and pull the image

 - [Docker Hub](https://hub.docker.com/r/asanrom/pmv)
 - [GitHub Packages](https://github.com/AgustinSRG/PersonalMediaVault/pkgs/container/personalmediavault)

Here is an example, if you choose Docker Hub:

```sh
docker pull asanrom/pmv
```

## Setup vault

Create a folder where you wish to install the vault, and create a file named `docker-compose.yml`, with the following content:

```yaml
version: '3.9'

services:

  pmv:
    image: asanrom/pmv
    ports:
      - '80:80'
      - '443:443'
    volumes:
      - './:/vault'
    restart: unless-stopped
    command: --daemon --clean --log-requests --skip-lock --vault-path /vault
```

Check the [server options](/docs/technical-documentation/server-options/) for more information of all the available options to run the server.

## Running the vault

In order to run the vault, run Docker compose:

```sh
docker compose up -d
```

Go to http://localhost to check out your vault. You can login with:

 - Username: `admin`
 - Password: `admin`

Change your password, and possibly username, and start using your vault.

If you want to stop the vault server, run the following command:

```sh
docker compose down
```
