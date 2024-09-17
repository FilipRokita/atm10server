# All the Mods 10 Server and playit.gg in Docker

## Overview
This guide explains how to run a Minecraft server for "All the Mods 10" using Docker. It also includes setup instructions for integrating a playit.gg tunnel to allow you and your friends to connect easily. **This configuration should also work with any CurseForge modpack by adjusting the server files accordingly.**

**Disclaimer:** This guide is tested with version `All The Mods 10-0.52` on `Ubuntu Server 22.04`. Other versions may not work as expected.

## Prerequisites
- Docker and Docker Compose installed on your server.
- Basic familiarity with Docker and command-line interfaces.
- An account with playit.gg.

## Setup

1. **Download Server Files**
   - Download the "All the Mods 10" server files from [CurseForge](https://www.curseforge.com/minecraft/modpacks/all-the-mods-10).

2. **Place Server Files**
   - Move the downloaded `.zip` file to the `modpacks` folder in your project directory.

3. **Create a playit.gg Account**
   - Sign up at [playit.gg](https://playit.gg) if you don’t already have an account.

4. **Set Up Docker-Based Agent**
   - Follow the instructions on playit.gg to configure a Docker-based agent. Obtain your secret key and create a tunnel. This will allow external connections to your Minecraft server.

5. **Configure Docker Compose**
   - Add your playit.gg secret key to the `docker-compose.yaml` file under the `playit` service's environment section. Replace `<INSERT PLAYIT.GG SECRET KEY HERE>` with your actual secret key.
   - Replace `<INSERT SERVER FILES .ZIP FILE NAME HERE>` with the actual name of the server files `.zip` file you downloaded e.g. `Server-Files-0.52.zip`.

## Getting Started

### Start the Server
To start the server in detached mode, run:
```bash
docker compose up -d
```

### Stop the Server
To stop the server and remove the containers, run:
```bash
docker compose down
```

### Access Minecraft Server Console
To access the Minecraft server's CLI, run:
```bash
docker attach atm10srv-mc-1
```

### Detach from Minecraft Server Console
To safely detach from the CLI without stopping the server, press `[Ctrl] + [P]` followed by `[Ctrl] + [Q]`.

## Uninstall

### Remove Folder
To remove the `atm10srv` folder and all its contents, run:
```bash
rm -rf atm10srv
```

### Clear Unused Docker Resources
**Warning:** This will remove all unused Docker containers, images, volumes, networks, and more. Use with caution.
```bash
docker system prune -a
```

## Troubleshooting
If you encounter any issues or have questions, consider consulting the documentation for Docker, playit.gg or itzg's Minecraft Server on Docker.
- [Docker Docs](https://docs.docker.com/)
- [playit.gg Docs](https://playit.gg/support/)
- [itzg's Minecraft Server on Docker Docs](https://docker-minecraft-server.readthedocs.io/)

---

**Date:** 2024-09-17  
**Author:** Filip Rokita

*Feel free to adjust the commands or configurations as needed.*
