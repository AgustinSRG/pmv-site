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
services:
  pmvd:
    hostname: "pmvd"
    image: "asanrom/pmv"
    ports:
      - "${VAULT_PORT}:8000"
    restart: unless-stopped
    volumes:
      - ${VAULT_PATH:-./vault}:/vault
      - ${VAULT_SSL_PATH:-./ssl}:/ssl:ro
    environment:
      - USING_PROXY=${USING_PROXY:-NO}
      - VAULT_INITIAL_USER=${VAULT_INITIAL_USER:-admin}
      - VAULT_INITIAL_PASSWORD=${VAULT_INITIAL_PASSWORD:-changeme}
      - SSL_CERT=${SSL_CERT:-}
      - SSL_KEY=${SSL_KEY:-}
    command: --daemon
      --clean
      --port 8000
      --skip-lock
      --vault-path /vault
      --cache-size ${VAULT_CACHE_SIZE:-1024}
      ${VAULT_EXTRA_OPTIONS:-}
```

Also, create a `.env` file, with the following content (modify the configuration depending on your needs):

```sh
####################################
# PersonalMediaVault configuration #
####################################

# Listening port
VAULT_PORT=8000

# Path where the vault will be stored
VAULT_PATH=./vault

# SSL (recommended)
#
# Running the vault with HTTP is the most secure option
# Obtain a key and a certificate for your domain
#
# Set VAULT_SSL_PATH to the path where the key and the certificate are stored
# This path will be mapped to /ssl in the container
# Set SSL_KEY and SSL_CERT to the key and certificate chain files respectively
# The files must be in the /ssl path (eg: /ssl/certificate.pem) and in PEM format

VAULT_SSL_PATH=./ssl

#SSL_KEY=/ssl/key.pem
#SSL_CERT=/ssl/certificate.pem

# Reverse proxy
#
# Sometimes is better to use a reverse proxy (line NGINX)
# as the frontend and forward the requests to the daemon
#
# If you are using it, set USING_PROXY to YES in order for
# the daemon to change the way it resolves the IP addresses of clients

USING_PROXY=NO

# Initial vault user
#
# If the vault has no users, an initial user will be created
#
# Set VAULT_INITIAL_USER and VAULT_INITIAL_PASSWORD
# for the username and password respectively
#
# Make sure to change them the first time you log into the vault.

VAULT_INITIAL_USER=admin
VAULT_INITIAL_PASSWORD=changeme

# Cache size
# You can modify it to accelerate the read speed
# but will also result in higher memory usage
# The recommended value is 1024

VAULT_CACHE_SIZE=1024

# Extra options
#
# You can set the following extra options,
# separating them with spaces:
#
#   --log-requests - Enables request logging
#   --debug - Enables debug logging (useful for troubleshooting)
#   --recover - Recovers non-indexed media assets.
#   --check-trash - Checks the vault (at startup) in order to find trash files. This option requires the vault credentials passed in the environment variables 'VAULT_USER' and 'VAULT_PASSWORD', in order to decrypt the vault files.
#   --remove-trash - Removes the trash files. Combine this option with '--check-trash'.
VAULT_EXTRA_OPTIONS=--log-requests
```

Check the [server options]({{< baseurl >}}docs/technical-documentation/server-options/) for more information of all the available options to run the server.

## Running the vault

In order to run the vault, run Docker compose:

```sh
docker compose up -d
```

Go to http://localhost to check out your vault. You can login with the credentials you specified in `VAULT_INITIAL_USER` and `VAULT_INITIAL_PASSWORD`.

Change your password, and possibly username, and start using your vault.

## Upgrading the image

If you want to  upgrade the image in order to use the latest version, wun:

```sh
docker compose pull
```

Then, to restart the vault, run:

```sh
docker compose up -d
```

## Stopping the vault

If you want to stop the vault server, run the following command:

```sh
docker compose down
```
