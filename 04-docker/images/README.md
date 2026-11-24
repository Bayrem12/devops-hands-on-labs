# Docker Images

## 1. What is a Docker Image?

A Docker image is a read-only template used to create containers.

An image can contain:
- Application files
- Dependencies
- Runtime environment
- Configuration

A container is created from an image.

## 2. Image Commands

| Command | Purpose |
|---|---|
| `docker images` | List locally available images |
| `docker rmi <image>` | Remove an image |
| `docker run <image>` | Create and start a container from an image |

### Examples

```bash
# List images
docker images

# Remove an image
docker rmi nginx

# Run a container from an image
docker run nginx
```

**Important:** Remove containers using an image before attempting to remove that image.

## 3. Image Layers

Docker images consist of read-only layers.

- Layers can be shared between images.
- Docker can reuse cached layers.
- Containers add a writable layer above the image layers.

## Remember

- Images are templates.
- Containers are running instances created from images.
- `docker images` lists local images.
- `docker rmi` removes images.
- Image layers are read-only.
