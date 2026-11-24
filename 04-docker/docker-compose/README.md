# Docker Compose

## 1. What is Docker Compose?

Docker Compose is a tool for defining and running multi-container applications using a YAML configuration file.

Instead of managing each container separately, Compose allows you to define the application services in one file.

## 2. Compose File Structure

A Compose file commonly defines services and volumes.

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"

volumes:
  app-data:
```

### Important YAML Rules

- Indentation defines the structure.
- Use spaces, not tabs.
- Lists use `-`.
- `services` contains the application services.
- `volumes` is a top-level section when declaring named volumes.

## 3. Important Compose Commands

| Command | Purpose |
|---|---|
| `docker compose up` | Create and start services |
| `docker compose up -d` | Start services in the background |
| `docker compose down` | Stop and remove containers and networks |
| `docker compose ps` | Display service status |
| `docker compose logs` | Display service logs |
| `docker compose config` | Validate and display the resolved configuration |

### Using a Specific Compose File

```bash
docker compose -f docker-compose-simple.yml up
```

- `-f` specifies the Compose file.
- `up` creates and starts the services.

## 4. Example: Voting Application

The project contains five services:

| Service | Role |
|---|---|
| `vote` | Voting interface |
| `result` | Displays voting results |
| `worker` | Processes votes |
| `redis` | Temporary vote queue |
| `db` | PostgreSQL database |

### Compose Configuration

The project's `docker-compose-simple.yml` defines:

- `vote` and `result` with published ports.
- `worker` using its application image.
- `redis` using `redis:alpine`.
- `db` using `postgres:15-alpine`.
- A named volume called `db-data` for PostgreSQL data.

### Port Mapping

```yaml
ports:
  - "8080:80"
```

Format:

```text
HOST_PORT:CONTAINER_PORT
```

### Environment Variables

```yaml
environment:
  POSTGRES_USER: postgres
  POSTGRES_PASSWORD: postgres
```

### Named Volume

```yaml
volumes:
  - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

The first `volumes` belongs to the database service. The second is the top-level volume declaration.

## 5. Running the Application

```bash
# Start the application
docker compose -f docker-compose-simple.yml up

# Start in the background
docker compose -f docker-compose-simple.yml up -d

# Check services
docker compose -f docker-compose-simple.yml ps

# View logs
docker compose -f docker-compose-simple.yml logs

# Stop and remove the Compose application
docker compose -f docker-compose-simple.yml down
```

## Remember

- Compose manages multiple services through one YAML file.
- `-f` selects a configuration file.
- `up` creates and starts services.
- `-d` runs in detached mode.
- YAML indentation matters.
- Named volumes help preserve database data.
