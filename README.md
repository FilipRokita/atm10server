# All the Mods 10 Server and playit.gg in Docker

## Overview
This guide explains how to run a Minecraft server for "All the Mods 10" using Docker. It also includes setup instructions for integrating a playit.gg tunnel to allow you and your friends to connect easily.

### This configuration should also work with ANY CurseForge modpack by adjusting the server files accordingly.

**Disclaimer:** Tested with `All The Mods 10-0.52` on `Ubuntu Server 22.04`.

## Prerequisites
- Git, Docker and Docker Compose installed on your server/machine.
- Basic familiarity with Docker and command-line interfaces.
- An account with playit.gg.

## Setup

1. **Clone the Repository**
   - To clone the repository, run: `git clone https://github.com/FilipRokita/minecraft-atm10-playitgg-docker`
   - To rename the folder to something shorter, run: `mv minecraft-atm10-playitgg-docker atm10srv`

2. **Download Server Files**
   - Download the "All the Mods 10" server files from [CurseForge](https://www.curseforge.com/minecraft/modpacks/all-the-mods-10).

3. **Place Server Files**
   - Move the downloaded `.zip` file to the `modpacks` folder in your project directory.

4. **Create a playit.gg Account**
   - Sign up at [playit.gg](https://playit.gg) if you don’t already have an account.

5. **Set Up Docker-Based Agent**
   - Follow the instructions on playit.gg to configure a Docker-based agent. Obtain your secret key and create a tunnel. This will allow external connections to your Minecraft server.

6. **Configure Docker Compose**
   - Add your playit.gg secret key to the `docker-compose.yaml` file under the `playit` service's environment section. Replace `<INSERT PLAYIT.GG SECRET KEY HERE>` with your actual secret key.
   - Replace `<INSERT SERVER FILES .ZIP FILE NAME HERE>` with the actual name of the server files `.zip` file you downloaded e.g. `Server-Files-0.52.zip`.

## Getting Started

### Start the Server
To start the server in detached mode, run:
```bash
docker compose up -d
```
**Note:** You must run this command inside the directory where the docker-compose.yaml file is located.

### Stop the Server
To stop the server and remove the containers, run:
```bash
docker compose down
```
**Note:** You must run this command inside the directory where the docker-compose.yaml file is located.

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
