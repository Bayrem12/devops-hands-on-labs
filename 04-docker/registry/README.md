# Docker Registry

## 1. What is a Docker Registry?

A Docker Registry is a storage and distribution system for Docker images.

It allows users to:
- Store Docker images.
- Push images to a registry.
- Pull images from a registry.
- Share images between environments.

By default, Docker uses **Docker Hub** as its default registry.

For example:

```bash
docker pull nginx
```

This pulls the `nginx` image from Docker Hub.

## 2. Docker Hub

Docker Hub is a hosted registry service provided by Docker.

Its features include:
- Public and private repositories.
- Automated image builds.
- Integration with GitHub and Bitbucket.
- Webhooks.
- Image tagging and versioning.
- Team collaboration and access control.
- Vulnerability scanning on supported plans.

## 3. Deploy a Local Docker Registry

Docker provides an open-source registry image that allows us to host our own registry.

### Run the Registry Server

```bash
docker run -d \
  -p 5000:5000 \
  --restart=always \
  --name my-registry \
  registry:2
```

### Command Breakdown

| Option | Purpose |
|---|---|
| `-d` | Runs the container in detached mode |
| `-p 5000:5000` | Maps host port 5000 to container port 5000 |
| `--restart=always` | Automatically restarts the container |
| `--name` | Assigns the name `my-registry` |
| `registry:2` | Uses the Docker Registry version 2 image |

The local registry is now accessible at:

```text
localhost:5000
```

**Note:** Authentication is not configured in this lab, so `docker login` is not required.

## 4. Push Images to a Local Registry

To push an image to a registry, we follow three steps:

1. Pull the image.
2. Tag the image with the registry address.
3. Push the tagged image.

### Push Nginx

**Step 1: Pull the image**

```bash
docker image pull nginx:latest
```

**Step 2: Tag the image**

```bash
docker image tag nginx:latest localhost:5000/nginx:latest
```

**Step 3: Push the image**

```bash
docker image push localhost:5000/nginx:latest
```

### Push HTTPD

```bash
docker image pull httpd:latest

docker image tag httpd:latest localhost:5000/httpd:latest

docker image push localhost:5000/httpd:latest
```

## 5. List Images in the Registry

The Registry HTTP API provides an endpoint to list repositories.

```bash
curl localhost:5000/v2/_catalog
```

This returns the repositories stored in the local registry.

## 6. Pull Images from a Local Registry

To pull an image from a specific registry, use:

```bash
docker pull REGISTRY_ADDRESS/IMAGE_NAME:TAG
```

Example:

```bash
docker pull localhost:5000/nginx:latest
```

This pulls the Nginx image from our local registry.

## 7. Important Concepts to Remember

- Docker Hub is Docker's default registry.
- A registry stores and distributes Docker images.
- `docker image tag` creates an additional image reference with a registry address.
- `docker image push` uploads an image to a registry.
- `docker pull` downloads an image from a registry.
- `localhost:5000` identifies our local registry in this lab.
- The registry used here
