# Docker Engine & Containers

## 1. Docker Engine

Docker Engine is the platform responsible for building and running containers.

### Main Components

| Component | Responsibility |
|---|---|
| Docker CLI | Accepts commands from the user |
| Docker Daemon (`dockerd`) | Manages Docker objects |
| Docker REST API | Allows the CLI and other clients to communicate with the daemon |
| containerd | Manages container lifecycle and runtime operations |
| runc | Starts containers using Linux kernel features |

### Execution Flow

```text
Docker CLI
    |
    v
Docker Daemon (dockerd)
    |
    v
containerd
    |
    v
runc
    |
    v
Linux Kernel
```

## 2. Linux Namespaces

Namespaces provide isolation by giving container processes separate views of system resources.

| Namespace | Purpose |
|---|---|
| PID | Isolates process IDs |
| Network | Isolates network interfaces and routing |
| IPC | Isolates inter-process communication |
| Mount | Provides a separate filesystem mount view |
| UTS | Isolates hostname and domain name |
| User | Isolates user and group IDs |

**Example:** A process can appear as PID 1 inside a container while having a different PID on the host.

## 3. Control Groups (cgroups)

Control groups manage and limit the resources available to containers.

They help control:
- CPU
- Memory
- Process count
- Block I/O

### Resource Options

| Option | Purpose |
|---|---|
| `--cpus` | Limit CPU usage |
| `--memory` | Set memory limit |
| `--cpuset-cpus` | Select CPU cores |
| `--memory-swap` | Configure memory and swap limit |
| `--pids-limit` | Limit the number of processes |

Example:

```bash
docker run --cpus=0.5 --memory=100m ubuntu
```

## 4. Container Lifecycle Commands

| Command | Purpose |
|---|---|
| `docker run <image>` | Create and start a container |
| `docker run -d <image>` | Run in detached mode |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker stop <container>` | Stop a running container |
| `docker rm <container>` | Remove a container |

### Practical Example

```bash
docker run -d --name blue-app kodekloud/simple-webapp:blue

docker ps

docker stop blue-app

docker rm blue-app
```

## Remember

- Docker Engine manages containers and related resources.
- Namespaces provide isolation.
- cgroups control resource usage.
- `docker run` creates and starts a container.
- `docker ps` shows running containers.
- `docker ps -a` also shows stopped containers.
