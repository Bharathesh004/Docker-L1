# 🐳 Docker Cheat Sheet: Your Container Command Arsenal

<div align="center">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Container](https://img.shields.io/badge/Container-Ready-success?style=for-the-badge)
![DevOps](https://img.shields.io/badge/DevOps-Enabled-blue?style=for-the-badge)

**From Zero to Docker Hero in 10 Commands** 🚀

*Because "It works on my machine" is no longer an excuse!*

</div>

---

## 📋 Table of Contents
- [🎯 Getting Started](#-getting-started)
- [🏗️ Building Images](#️-building-images)
- [🚀 Running Containers](#-running-containers)
- [🔍 Inspection & Monitoring](#-inspection--monitoring)
- [🧹 Cleanup Operations](#-cleanup-operations)
- [☁️ Publishing to Docker Hub](#️-publishing-to-docker-hub)
- [🎼 Docker Compose Magic](#-docker-compose-magic)

---

## 🎯 Getting Started

### Pull Your First Image
Think of this as downloading an app, but for containers!

```bash
# Pull any image from Docker Hub
docker pull <image_name>

# Example: Let's grab Ubuntu
docker pull ubuntu
```

### Create Your First Container
Time to bring that image to life! 🎭

```bash
# Run interactively with a terminal
docker run -it ubuntu

# -it = Interactive Terminal (you can type commands inside!)
```

---

## 🏗️ Building Images

### Build From Dockerfile
Turn your code into a portable, reproducible container! 📦

```bash
# Basic build command
docker build -t <image-name> <path-to-dockerfile>

# Real world example
docker build -t demo-docker .
# The '.' means "Dockerfile is right here!"
```

### View Your Image Collection
See all the images you've built or pulled 🖼️

```bash
docker images
```

**Pro Tip:** Think of images as **blueprints** and containers as **houses built from those blueprints**! 🏠

---

## 🚀 Running Containers

### Basic Run
Launch your container into action!

```bash
docker run <image-name>

# Example
docker run demo-docker
```

### Interactive Shell Access
Need to peek inside? Open a shell! 🐚

```bash
docker run -it demo-docker sh

# Now you're INSIDE the container! 
# It's like SSH-ing into a tiny Linux machine
```

### Port Mapping (The Bridge!) 🌉
Connect your local machine to the container's port

```bash
docker run -p <host-port>:<container-port> <image-name>

# Example: Access container's port 5173 via localhost:5173
docker run -p 5173:5173 react-docker
```

**What's happening?** 
- Host Port (5173) → Your computer
- Container Port (5173) → Inside Docker
- They're now connected! 🔗

### Volume Mounting (Live Sync!) 🔄
Make changes on your computer, see them instantly in the container!

```bash
docker run -p 5173:5173 \
  -v "$(pwd):/app" \
  -v /app/node_modules \
  react-docker
```

**Breaking it down:**
- `-v "$(pwd):/app"` → Sync current directory to /app in container
- `-v /app/node_modules` → Keep node_modules inside container (faster!)
- Result: **Hot reload works!** 🔥

---

## 🔍 Inspection & Monitoring

### List Running Containers
Who's currently active? 👀

```bash
# Only running containers
docker ps

# All containers (running + stopped)
docker ps -a
```

**Quick Reference:**
- `CONTAINER ID` → Unique identifier
- `IMAGE` → Which blueprint was used
- `STATUS` → Up or Exited
- `PORTS` → Port mappings

---

## 🧹 Cleanup Operations

### Remove All Stopped Containers
Spring cleaning for Docker! 🧼

```bash
docker container prune

# Docker will ask: "Are you sure? (y/n)"
# This frees up disk space!
```

**Warning:** This deletes ALL stopped containers. Make sure you don't need them!

---

## ☁️ Publishing to Docker Hub

### Login to Docker Hub
Authenticate yourself! 🔐

```bash
docker login

# Enter your username and password
# You're now connected to Docker Hub!
```

### Tag Your Image
Give your image a proper name for publishing 🏷️

```bash
docker tag <image-name> <username>/<image-name>

# Example
docker tag react-docker bharathesh004/react-docker
```

**Format:** `username/repository-name:tag`
- Default tag is `latest` if not specified

### Push to Docker Hub
Share your creation with the world! 🌍

```bash
docker push <username>/<image-name>

# Example
docker push bharathesh004/react-docker
```

**Now anyone can run:**
```bash
docker pull bharathesh004/react-docker
```

---

## 🎼 Docker Compose Magic

### Initialize Docker Compose
Let Docker create the boilerplate for you! ✨

```bash
docker init

# This generates:
# ✓ Dockerfile
# ✓ docker-compose.yml
# ✓ .dockerignore
```

**Docker Compose** = Manage multiple containers with ONE command!

### Build & Run with Compose
One command to rule them all! 👑

```bash
docker-compose up

# Builds images + Creates containers + Starts everything
# Add -d flag for detached mode (runs in background)
docker-compose up -d
```

**Stop everything:**
```bash
docker-compose down
```

---

## 🎓 Quick Command Reference

| Command | What It Does | When to Use |
|---------|--------------|-------------|
| `docker pull` | Download image | Getting base images |
| `docker build` | Create custom image | Building your app |
| `docker run` | Start container | Running your app |
| `docker ps` | List containers | Checking status |
| `docker images` | List images | See what's available |
| `docker login` | Authenticate | Before pushing |
| `docker push` | Upload to Hub | Sharing images |
| `docker-compose up` | Multi-container setup | Complex apps |

---

## 💡 Pro Tips

1. **Use .dockerignore** → Like .gitignore, but for Docker (exclude node_modules, .git, etc.)
2. **Tag your images** → `image:v1.0` is better than `image:latest`
3. **Multi-stage builds** → Keep images small and secure
4. **Use Alpine images** → Smaller = Faster downloads
5. **Clean up regularly** → `docker system prune` removes unused data

---

## 🤝 Contributing

Found a better way to do something? Got a cool Docker trick? 

**Pull requests welcome!** 🎉

---

## 📚 Resources

- [Official Docker Docs](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Dockerfile Best Practices](https://docs.docker.com/develop/dev-best-practices/)

---

<div align="center">

**Made with ❤️ and lots of ☕**

*"Docker: Because configurations shouldn't be a nightmare"* 🌙

⭐ **Star this repo if it helped you!** ⭐

</div>