Installing Docker
---
🏠 [Home](/workshops/preparations/README.md)

[Docker](https://www.docker.com/) is a container runtime and is required before we do anything else. Most, if not all, kubernetes distributions you install locally run inside containers using Docker. Most operating systems are supported including Linux, macOS and Windows.

## Linux
On Linux systems Docker is installed on a per-distro basis. So you'll need to follow the instructions that matches your system. 
1. Head on over [here ➚](https://docs.docker.com/engine/install/#server) and make sure to install Docker. 
2. If you can't find your distro on that list, such as Gentoo ☠️ for example, then you can allways install Docker using [the binary installation](https://docs.docker.com/engine/install/binaries/).

## macOS
If you're running macOS then you'll need to download and install `Docker Desktop`. 
1. Head on over [here ➚](https://docs.docker.com/desktop/mac/install/) and download Docker Desktop.
2. Run the installer to install Docker Desktop on your Mac. Further installation documentation is included in the download link

## Windows
There's a flavor of Docker Desktop for Windows users aswell. So if you're rockin' Windows then do as following
1. Head on over [here ➚](https://docs.docker.com/desktop/windows/install/) and download the installer.
2. Run the installer to install Docker Desktop. Further installation documentation is included in the download link

## Verify install
Now, make sure that everything is working by issuing `docker info` in a terminal. The ouput should be something similar to this:
```
$ docker info
Client:
 Context:    default
 Debug Mode: false
 Plugins:
  compose: Docker Compose (Docker Inc., v2.2.3)
  scan: Docker Scan (Docker Inc., v0.16.0)
WARNING: Plugin "/Users/amir/.docker/cli-plugins/docker-app" is not valid: failed to fetch metadata: fork/exec /Users/amir/.docker/cli-plugins/docker-app: no such file or directory
WARNING: Plugin "/Users/amir/.docker/cli-plugins/docker-buildx" is not valid: failed to fetch metadata: fork/exec /Users/amir/.docker/cli-plugins/docker-buildx: no such file or directory

Server:
 Containers: 23
  Running: 1
  Paused: 0
  Stopped: 22
 Images: 62
...
```