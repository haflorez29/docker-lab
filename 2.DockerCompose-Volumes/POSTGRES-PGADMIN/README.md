# PostgreSQL + PgAdmin with Docker Compose

PostgreSQL database with PgAdmin graphical interface for management, running with Docker Compose.

## Project focus

This folder is a Docker Compose exercise for volumes and database management. It shows how to run PostgreSQL and PgAdmin together with persistent storage.

## What I learned

- Use Docker Compose for database and admin UI orchestration
- Keep PostgreSQL data with a persistent named volume
- Connect PgAdmin to PostgreSQL through the Compose network
- Stop and remove services and data with `docker-compose down -v`

## Description

This project provides:

- **PostgreSQL 15.1** - Relational database
- **PgAdmin 4** - Web interface to manage PostgreSQL
- **Persistent volumes** - Data is maintained between restarts
- **Docker Compose** - Simple container orchestration

## Prerequisites

- **Docker** installed
- **Docker Compose** installed (version 3 or higher)

## Quick Start

### 1. Enter the project folder

```bash
cd POSTGRES-PGADMIN
```

### 2. Run Docker Compose

```bash
docker-compose up -d
```

### 3. Verify that services are running

```bash
docker-compose ps
```

## Credentials

### PostgreSQL
- **Host:** `postgres_database` (from other containers) or `localhost` (from your machine)
- **Port:** `5432`
- **Username:** `postgres`
- **Password:** `123456`

### PgAdmin
- **URL:** `http://localhost:8080`
- **Email:** `superman@google.com`
- **Password:** `123456`

### Steps to connect in PgAdmin:

1. Right-click on "Servers" → "Create" → "Server"
2. **"General" Tab:**
   - Name: `PostgreSQL 15`
3. **"Connection" Tab:**
   - Host: `postgres_database`
   - Port: `5432`
   - Username: `postgres`
   - Password: `123456`
4. Click "Save"

## Stop services

```bash
docker-compose down
```

## Remove everything (including volumes)

```bash
docker-compose down -v
```

**Warning:** This will delete the database data.

## Volume structure

```
POSTGRES-PGADMIN/
├── postgres/                    # PostgreSQL data
├── pgadmin/                     # PgAdmin config
│   ├── azurecredentialcache/
│   ├── sessions/
│   └── storage/
└── docker-compose.yml           # Compose config
```

## Restart services

```bash
docker-compose restart
```

## Logs

```bash
docker-compose logs

docker-compose logs postgres_database
docker-compose logs pgadmin_container

docker-compose logs -f
```

## References

- [PostgreSQL Docs](https://www.postgresql.org/docs/)
- [PgAdmin Docs](https://www.pgadmin.org/docs/)
- [Docker Compose Docs](https://docs.docker.com/compose/)

## Course Reference

This project was created following the course:

**[Docker - Gu�a pr�ctica de uso para desarrolladores](https://www.udemy.com/course/docker-kubernetes-curso-completo/)**

By **Fernando Herrera**

It's a lab exercise from the course adapted for learning Docker Compose with PostgreSQL and PgAdmin.

## Learnings
- docker compose files
- networks
- use named volumes
