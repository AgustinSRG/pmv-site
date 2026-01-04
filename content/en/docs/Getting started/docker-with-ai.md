---
title: Run with Docker (with AI features)
description: >
  Guide on how to run PersonalMediaVault with Docker
  enabling the available AI features
categories: [Guides, Installation, Technical]
tags: [guides, installation, technical, docker]
---

This guide explains how to run PersonalMediaVault with Docker, enabling the available AI features (semantic search and search by image).

By default, PersonalMediaVault runs without AI features. You must add the missing components and configuration settings in order to enable them.

This opt-in approach has been chosen due to the high cost of the dependencies to enable the features, versus the actual utility of the features:

 - The size is too high (+10GB in dependencies).
 - It increases the memory usage and also the CPU / GPU usage.

If you enable AI features, you'll get the following features:

 - Semantic search: Search images with natural language. For example: If you are looking for pictures of your pet cat, you can type "Cat" and it will find images where a cat appears. This can make way easier to find the images you are looking for, specially if you do not like to classify your images with tags and albums.
 - Search by image: Select an image in your computer and obtain the most similar images available in your vault. This can be used to check if you already uploaded a particular image, or in order to find related images.

## Pull images

For this Docker Compose setup, you will need the following images:

 - [asanrom/pmv](https://hub.docker.com/r/asanrom/pmv) - The PersonalMediaVault main image.
 - [asanrom/pmv-ai-service](https://hub.docker.com/r/asanrom/pmv-ai-service) - A Python service that provides access to the AI models.
 - [qdrant/qdrant](https://hub.docker.com/r/qdrant/qdrant) - A vector database to index the images and perform queries.

To pull them, type:

```sh
docker pull asanrom/pmv
docker pull asanrom/pmv-ai-service
docker pull qdrant/qdrant
```

## Setup vault

Create a folder where you wish to install the vault, and create a file named `docker-compose.yml`, with the following content:

```yaml
services:

  # Qdrant vector database
  pmv_qdrant:
    hostname: "pmv-qdrant"
    image: qdrant/qdrant
    networks:
      - pmv_with_ai_network
    ports:
      - '6334'
    volumes:
      - ./qdrant-db:/qdrant/storage
    restart: unless-stopped
    environment:
      - QDRANT__LOG_LEVEL=${QDRANT_LOG_LEVEL:-INFO}
      - QDRANT__SERVICE__API_KEY=${QDRANT_API_KEY:-change_me}
      - QDRANT__GRPC_PORT=6334

  # AI service for encoding text and images into vectors
  pmv_ai:
    hostname: "pmv-ai"
    image: asanrom/pmv-ai-service
    networks:
      - pmv_with_ai_network
    ports:
      - '8080'
    volumes:
      - ./ai-models:/home/app/.data
    restart: unless-stopped
    environment:
      - LOGLEVEL=${AI_SERVICE_LOG_LEVEL:-INFO}
      - API_AUTHORIZATION=${AI_SERVICE_AUTH_TOKEN:-}
      - CLIP_MODEL_NAME=${CLIP_MODEL_NAME:-ViT-B/32}

  # PersonalMediaVault daemon
  pmvd:
    hostname: "pmvd"
    image: "asanrom/pmv"
    networks:
      - pmv_with_ai_network
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
      - SEMANTIC_SEARCH_ENABLED=YES
      - QDRANT_HOST=pmv-qdrant
      - QDRANT_PORT=6334
      - QDRANT_API_KEY=${QDRANT_API_KEY:-change_me}
      - QDRANT_USE_TLS=NO
      - QDRANT_INITIAL_SCAN=YES
      - CLIP_API_BASE=http://pmv-ai:8080/clip
      - CLIP_API_AUTH=${AI_SERVICE_AUTH_TOKEN:-}
      - CLIP_IMAGE_SIZE_LIMIT_MB=25
    command:
      --daemon
      --clean
      --port 8000
      --skip-lock
      --vault-path /vault
      --cache-size ${VAULT_CACHE_SIZE:-1024}
      ${VAULT_EXTRA_OPTIONS:-}

networks:
  pmv_with_ai_network:
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

# Qdrant log level
# Can be: ERROR, WARNING, INFO, DEBUG

QDRANT_LOG_LEVEL=INFO

# Qdrant API key
# Change it to a random string for security

QDRANT_API_KEY=change_me

# AI service log level
# Can be: ERROR, WARNING, INFO, DEBUG

AI_SERVICE_LOG_LEVEL=INFO

# AI service authorization token
# Change it to a random string for security

AI_SERVICE_AUTH_TOKEN=change_me

# CLIP model to use
# Available models: RN50, RN101, RN50x4, RN50x16, RN50x64, ViT-B/32, ViT-B/16, ViT-L/14 and ViT-L/14@336px

CLIP_MODEL_NAME=ViT-B/32
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
