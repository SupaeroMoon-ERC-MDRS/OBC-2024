# Docker Container how-to guide for OBC

For our project we need to let communicate two SBCs: Raspberry Pi 5 and NVIDIA Jetson Orin Nano. To do that we will use docker containers including ROS 2 Humble distribution. The development can be easily handled with Visual Studio Code.

## Prerequisites

1. **Docker** installed on your system. ([Install Docker](https://docs.docker.com/get-docker/))
2. **Visual Studio Code (VS Code)** installed. ([Download VS Code](https://code.visualstudio.com/))
3. **Dev Containers extension** installed in VS Code.
   - Open VS Code and go to the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X` on macOS).
   - Search for `Dev Containers` by Microsoft and install it.

## Steps to Use Docker Containers in VS Code

### 1. Start Docker

Ensure that Docker is running on your system. You can verify this by running:

```bash
docker --version
```

### 2. Open a Remote Window

There is a _devcontainer_ directory for each SBC, being: **rasp** and **jetson**. Be sure to open the directory target of the development (eg. use _rasp_ container for communication scripts).

On the left hand-side part of the bottom-bar you will find a green button `><`, click it and go to `Reopen in Container`.

Once done, the environment is automatically created in docker, with both _rasp_ and _jetson_ container running, with one of them opened in the VSC remote window. The internal docker network is set up as-well and defined as **obc_network**.

### 3. Use the Remote Window

Now you should be inside a remote window of VSC. At this point you have the possibility of viewing the shell inside the container opening a new terminal in this window.

The file system is composed of a set of directories including ROS and the OS.
**OBC** and other sub-teams should have _r-w-x_ access only to the directory `workspace`, defined as the workdirectory of the container.

---

### More information about images and containers

Everything is handled in the directories `.devcontainer`. The containers' images are first built using a common `Dockerfile` and then run by VSC through the `dockercontainer.json` file
using the configuration in the `docker-compose.yml` file instead.

The procedure can be similarly done in a terminal by more simply running:

```bash
docker compose up -d
```

although, for development purposes, is recommended to have the environment handled in VSC.
