# Docker Storage & Volumes

## 1. Docker Storage Location

On Linux, Docker stores most of its data under:

```bash
/var/lib/docker/
```

Common directories:

| Directory | Purpose |
|---|---|
| `containers/` | Container data and metadata |
| `image/` | Image metadata and layers |
| `volumes/` | Docker-managed volumes |
| `overlay2/` | Filesystem data for the overlay2 storage driver |

## 2. Image and Container Layers

Docker images contain read-only layers.

When a container starts, Docker adds a writable layer on top of the image.

**Important:** Changes stored only in the container's writable layer are lost when that container is removed.

## 3. Docker Volumes

Volumes are managed by Docker and allow data to persist beyond the lifetime of a container.

### Create a Volume

```bash
docker volume create datavolume
```

### Mount a Volume

```bash
docker run -v datavolume:/var/lib/mysql mysql
```

The volume name is on the left, and the container path is on the right.

## 4. Bind Mounts

Bind mounts connect an existing directory or file on the host to a location inside a container.

### Syntax

```bash
-v HOST_PATH:CONTAINER_PATH
```

### Example

```bash
docker run -v /opt/data:/var/lib/mysql \
  -d \
  --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=replace-with-a-local-demo-password \
  mysql
```

| Part | Purpose |
|---|---|
| `/opt/data` | Host directory |
| `/var/lib/mysql` | Container directory |
| `-v` | Mounts the directory |
| `-e` | Sets an environment variable |
| `-d` | Runs in detached mode |
| `--name` | Sets the container name |

## 5. Volumes vs Bind Mounts

| Feature | Docker Volume | Bind Mount |
|---|---|---|
| Managed by | Docker | Host filesystem |
| Source | Docker-managed location | Existing host path |
| Main purpose | Persistent container data | Share host files with containers |

## Remember

- The container writable layer is temporary.
- Volumes are managed by Docker.
- Bind mounts use existing host paths.
- Both methods can persist data beyond a container's lifetime.
- Removing a container does not automatically remove a separately managed volume.
