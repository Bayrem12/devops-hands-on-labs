# Docker Networking

## 1. What is Docker Networking?

Docker networking allows containers to communicate with:
- Other containers
- The Docker host
- External networks

It also provides network isolation between containers.

## 2. Default Docker Networks

Docker provides three default network drivers:

| Network | Description |
|---|---|
| `bridge` | Connects containers through a private network |
| `host` | Shares the host's network stack |
| `none` | Disables external container networking |

### Bridge Network

- Default network used by containers when no network is specified.
- Uses a virtual bridge interface, commonly `docker0`.
- Containers receive internal IP addresses.
- Port mapping allows external access.

```bash
docker run -d --name web nginx
```

### Host Network

Shares the host's network stack.

```bash
docker run --network host nginx
```

Port mapping is not required with host networking.

### None Network

Disables external container networking.

```bash
docker run --network none nginx
```

## 3. User-Defined Bridge Networks

User-defined bridge networks allow containers to communicate in an isolated network.

### Create a Network

```bash
docker network create my-network
```

Create a network with a custom subnet:

```bash
docker network create \
  --driver bridge \
  --subnet 182.18.0.0/16 \
  custom-isolated-network
```

### List Networks

```bash
docker network ls
```

### Inspect a Network

```bash
docker network inspect my-network
```

## 4. Running Containers on a Specific Network

You can connect a container to a network when creating it using `--network`.

### Practical Example

```bash
docker run \
  -e DB_Host=mysql-db \
  -e DB_Password=db_pass123 \
  --name web-app \
  -p 38080:8080 \
  --network my-network \
  -d existing-image
```

### Command Breakdown

| Option | Purpose |
|---|---|
| `-e` | Sets an environment variable |
| `--name` | Assigns a container name |
| `-p` | Maps a host port to a container port |
| `--network` | Connects the container to a specified network |
| `-d` | Runs the container in detached mode |

### Container-to-Container Communication

If the database container is named `mysql-db` and both containers are connected to the same user-defined bridge network, the application can use `mysql-db` as its database hostname.

## 5. Port Mapping

Port mapping allows external traffic to reach a container service.

### Syntax

```bash
docker run -p HOST_PORT:CONTAINER_PORT nginx
```

Example:

```bash
docker run -d -p 8080:80 nginx
```

- Host port: `8080`
- Container port: `80`

## 6. Network Management Commands

| Command | Purpose |
|---|---|
| `docker network ls` | List Docker networks |
| `docker network create` | Create a network |
| `docker network inspect` | Display network details |
| `docker network rm` | Remove a network |

## 7. Networking Under the Hood

Docker networking uses Linux kernel mechanisms.

| Component | Purpose |
|---|---|
| Network namespaces | Isolate container network resources |
| Virtual Ethernet (veth) pairs | Connect network namespaces to other interfaces |
| Bridge interface | Connect containers on a bridge network |

## Remember

- Docker provides `bridge`, `host`, and `none` network drivers by default.
- User-defined bridge networks provide container name resolution.
- Containers on the same user-defined network can communicate using container names.
- `--network` connects a container during creation.
- `-p` publishes container ports.
- Use `docker network inspect` to investigate network configuration.