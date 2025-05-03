---
layout: post
title: "Docker Desktop on Windows WSL2"
date: 2025-05-02 11:30:00
authors:
- brucejia
tags: 
  - docker
  - wsl2
description: "How does Docker Desktop run on Windows with WSL2"
categories: "docker"
series:
- "Cloud Native"
---


# Docker Desktop on Windows WSL2

Docker Desktop on windows depends on WSL2 technology. Because you know Docker depends on Linux kernel supports like namespaces and cgroup. To implement these on Windows, one way is to use a virtual machine of Linux, another way is to use WSL2 or alike virtualization technoligies.

Previous version of Docker Desktop used Oracle VirtualBox virtual machines as host of docker containers. And now Docker Desktop by default uses WSL2 as it's a more lightweight approach on Windows.

Start your Windows OS and make sure Docker Desktop is not started yet, you can use this command to check status of the WSL distros. Note that `docker-desktop` distro is not running.

```
PS C:\Users\brucejia> wsl --list -v
```

```
  NAME                    STATE           VERSION
* Ubuntu-24.04            Stopped         2
  rancher-desktop         Stopped         2
  rancher-desktop-data    Stopped         2
  docker-desktop          Stopped         2
```

Then start Docker Desktop manually with GUI or with command line.

```
PS C:\Users\brucejia> docker desktop start
✓ Starting Docker Desktop
```

Then check WSL2 distro status again.

```
PS C:\Users\brucejia> wsl --list -v
```

```
  NAME                    STATE           VERSION
* Ubuntu-24.04            Running         2
  rancher-desktop         Stopped         2
  rancher-desktop-data    Stopped         2
  docker-desktop          Running         2
```

