# Foundry VTT - Docker

[![amd64](https://img.shields.io/docker/v/cryptoxic/fvtt-docker?arch=amd64&label=amd64&style=flat-square&filter=!latest)](https://hub.docker.com/r/cryptoxic/fvtt-docker/tags)
[![arm64](https://img.shields.io/docker/v/cryptoxic/fvtt-docker?arch=arm64&variant=v8&label=arm64&style=flat-square&filter=!latest)](https://hub.docker.com/r/cryptoxic/fvtt-docker/tags)
[![s390x](https://img.shields.io/docker/v/cryptoxic/fvtt-docker?arch=s390x&label=s390x&style=flat-square&filter=!latest)](https://hub.docker.com/r/cryptoxic/fvtt-docker/tags)

## Foundry VTT - Docker

This repository hosts the Foundry VTT `Dockerfile` for [cryptoxic/fvtt-docker](https://hub.docker.com/r/cryptoxic/fvtt-docker) on Docker Hub and [ghcr.io/kryptoxic/fvtt-docker](https://github.com/Kryptoxic/fvtt-docker/pkgs/container/fvtt-docker) on the GitHub Container Registry.

> Originally created by [BenjaminPrice](https://github.com/BenjaminPrice/fvtt-docker), based on the original [direckthit/fvtt-docker](https://hub.docker.com/r/direckthit/fvtt-docker) image. This fork is maintained by [Kryptoxic](https://github.com/Kryptoxic) following the archival of the upstream repository.

> [Foundry VTT](https://foundryvtt.com/) is a virtual tabletop for playing tabletop RPG games such as Dungeons & Dragons 5e.

A basic `docker-compose.yaml` file is included to get things up and running quickly.

### **Note**
At the request of the author of Foundry VTT, the source code for Foundry VTT is not included in this image. 

You will need to manually download the zip file from your Foundry VTT account on the [official Foundry VTT website](https://foundryvtt.com/).

---

## **Recommended Hosting**

Hosting your server on a dedicated server is recommended. These can be quite cheap.

If you don't have a preferred provider, a $5 Ubuntu server from either of the below options are good considerations.

### **Hosting Options**

#### Linode (Akamai)
A great cheap provider with servers all around the globe. They're one of the older VPS providers still around.

[Sign Up](https://www.linode.com/)

#### Digital Ocean
Another great cheap provider with servers all around the globe.

[Sign Up](https://www.digitalocean.com/)

---

## **Installation**

## Prerequisites

- [Docker](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Instructions

### Step 0 - Install Prerequisites

***Ensure you have both Docker and Docker Compose installed by following the directions in the links above.***

### Step 1 - Download the `docker-compose.yaml` file

Manually download it or use the command below

```shell
wget https://raw.githubusercontent.com/Kryptoxic/fvtt-docker/master/docker-compose.yaml
```

### Step 2 - Download the Foundry VTT Zip File

- Navigate to your User Profile page and find your Software Download Links on your license page.
- Download the `Node.js` version.
- Save it to the same directory as the `docker-compose.yaml` file from the previous step.

### Step 3 - Create your data directory

This directory is where your games, images, etc will all be stored and persisted when the docker container is restarted.

Either manually create the directory or use this shell command (linux/mac/WSL only) to create the directory in your user home:

```shell
mkdir $HOME/foundryvtt-data/
```

### Step 4 - Create your app directory (optional)

This is where you can place your custom login screen. You only need to perform this step if you want a custom login screen on foundryVTT.

Either manually create the directory or use this shell command (linux/mac/WSL only) to create the directory in your user home:

```shell
mkdir $HOME/foundryvtt-app/
```

### Step 5 - Modify the `docker-compose.yaml` file

#### Set your data directory by modifying this line:

```yaml
- /path/to/your/foundry/data/directory:/data/foundryvtt
```

Example:

```yaml
- /home/player1/foundryvtt-data:/data/foundryvtt
```

#### Set your download directory (where you saved your zip file) by modifying this line:

```yaml
- /path/to/your/foundry/zip/file:/host
```

Example:

```yaml
- /home/player1/downloads:/host
```

#### Set your app directory (where the app and login screen resides) by modifying this line:

```yaml
- /path/to/your/foundry/app/file:/opt/foundryvtt/resources/app
```

Example:

```yaml
- /home/player1/foundryvtt-app:/opt/foundryvtt/resources/app
```

### Step 6 - Run the server

```shell
docker-compose up -d
```

### Step 7 - Access the server

Navigate to your server in your webbrowser (by IP address, is recommended)

`http://127.0.0.1:30000/`

Replace `127.0.0.1` with your own IP address.


### Step 8 - Customize your login screen

you can customize your login screen using a fix such as this one:
[prettier login screen](https://github.com/TheEpicSnowWolf/Foundry-VTT-Prettier-Login-Screen)

---

## **Pinning to a Specific Version**

The provided `docker-compose.yaml` uses the `:latest` tag, which always tracks the most recent build of `master`. For a more stable deployment, pin to a tagged release by updating the `image:` line in your `docker-compose.yaml`:

```yaml
image: cryptoxic/fvtt-docker:1.0.0
```

Available versions are listed on the [Docker Hub tags page](https://hub.docker.com/r/cryptoxic/fvtt-docker/tags) and the [GHCR package page](https://github.com/Kryptoxic/fvtt-docker/pkgs/container/fvtt-docker).

## **Using GitHub Container Registry Instead**

The same multi-architecture image is published to both Docker Hub and the GitHub Container Registry. To pull from GHCR instead, replace the `image:` line in `docker-compose.yaml` with:

```yaml
image: ghcr.io/kryptoxic/fvtt-docker:latest
```

## **Supported Architectures**

Each tagged image is built for the following platforms:

- `linux/amd64`
- `linux/arm64/v8`
- `linux/s390x`

