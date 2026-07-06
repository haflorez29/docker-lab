# Docker Lab - Init Projects Guide

This folder holds the learning projects from the Docker course. It is a simple guide that explains what each project is, what was learned, and how the commands were executed.

## What this project is

- A practical Docker lab folder
- A place to remember how to run containers manually and with Docker Compose
- A guide for using volumes, networks, and service coordination
- A reminder of the real commands used during the exercises

## Projects in this folder

### 1. NestJS GraphQL App (`nest-graphql`)

This project was used to run the app container manually from the image. It shows how to download or use the image, mount code, and interact with GraphQL.

**What I learned:**
- Run a Docker container manually with `docker container run`
- Mount the project folder into the container with `-v`
- Expose ports and access GraphQL at `localhost`
- Stop and remove the container when finished
- Use the container shell command to install and start the app

**Commands used:**
```bash
cd nest-graphql
docker container run \
  --name nest-app \
  -w /app \
  -p 80:3000 \
  -v "$(pwd)":/app \
  node:16-alpine3.16 \
  sh -c "yarn install && yarn start:dev"

docker container stop nest-app
docker container rm nest-app
```

**Access:**
- GraphQL Playground: `http://localhost:3000/graphql`

---

### 2. Pokemon App with Docker Compose (`pokemon-app`)

This project shows how Docker Compose can coordinate more than one image. It runs the NestJS app, MongoDB, and Mongo Express together, with a volume to save data.

**What I learned:**
- Use `docker-compose up -d` to start multiple services together
- Connect the app service to MongoDB and Mongo Express
- Create and use persistent volumes for data
- Use Compose to manage service connections on a shared network

**Commands used:**
```bash
cd pokemon-app
docker-compose up -d
docker-compose down
docker-compose down -v
```

**Access:**
- Pokemon app: `http://localhost:3000`
- Mongo Express: `http://localhost:8080`

---

### 3. PostgreSQL + PgAdmin Stack (`POSTGRES-PGADMIN`)

This project was used to run a PostgreSQL database and PgAdmin UI using Docker Compose. It teaches how to use a named volume and a managed database network.

**What I learned:**
- Run a database stack with Docker Compose
- Connect PgAdmin to PostgreSQL inside the Compose network
- Use a named volume for persistent database data
- Remove containers and volumes safely when needed

**Commands used:**
```bash
cd POSTGRES-PGADMIN
docker-compose up -d
docker-compose ps
docker-compose down
docker-compose down -v
```

**Access:**
- PgAdmin: `http://localhost:8080`
- PostgreSQL: `localhost:5432`

---

## Main lessons learned

- Manual Docker is useful for testing a single service and learning container commands.
- Docker Compose is useful for coordinating multiple containers and connecting services automatically.
- Volumes keep data safe when containers stop or restart.
- Networks let containers communicate by service name inside Compose.
- Use the exact commands from the lab to repeat the steps later.

## Useful commands

```bash
# Check Docker and Compose versions
docker --version
docker-compose --version

# List running containers
docker container ls

# List all images
docker images

# View logs
docker logs container-name
docker logs -f container-name

# Stop containers
docker container stop container-name

# Remove containers
docker container rm container-name

# Remove stopped containers
docker container prune

# Remove unused images
docker image prune

# Docker Compose commands
docker-compose up -d
docker-compose logs -f
docker-compose ps
docker-compose down
docker-compose down -v
docker-compose restart

# Docker network commands
docker network create network-name
docker network inspect network-name
docker network ls
```

## Quick reference

| Project | Type | Purpose | Main commands | Notes |
|--------|------|---------|---------------|-------|
| nest-graphql | Manual Docker | Run NestJS GraphQL app manually | `docker container run`, `docker container stop`, `docker container rm` | Manual container run, volume mount, GraphQL access |
| pokemon-app | Docker Compose | Run app + MongoDB + Mongo Express | `docker-compose up -d`, `down`, `down -v` | Compose coordinates services and volumes |
| POSTGRES-PGADMIN | Docker Compose | Run PostgreSQL + PgAdmin | `docker-compose up -d`, `ps`, `down`, `down -v` | Compose stack with persistent database data |

## Notes

- In `nest-graphql`, the main focus was running the container manually and using an image with local code.
- In `pokemon-app`, the focus was on using Docker Compose to manage multiple images and service connections.
- In `POSTGRES-PGADMIN`, the focus was on database setup, PgAdmin access, and using volumes for persistent data.

## References

- Docker docs: https://docs.docker.com/
- Docker Compose docs: https://docs.docker.com/compose/
- NestJS docs: https://docs.nestjs.com/
- MongoDB docs: https://docs.mongodb.com/
- PostgreSQL docs: https://www.postgresql.org/docs/

## Course reference

These projects follow the course: **Docker - Guía práctica de uso para desarrolladores** by Fernando Herrera.

It is a learning exercise to practice Docker, manual containers, Compose, volumes, and networks.
