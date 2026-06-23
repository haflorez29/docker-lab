# PostgreSQL + PgAdmin with Docker Compose

PostgreSQL database with PgAdmin graphical interface for management, running with Docker Compose.

## 📋 Description

This project provides:

- **PostgreSQL 15.1** - Relational database
- **PgAdmin 4** - Web interface to manage PostgreSQL
- **Persistent volumes** - Data is maintained between restarts
- **Docker Compose** - Simple container orchestration

## 🚀 Prerequisites

- **Docker** installed
- **Docker Compose** installed (version 3 or higher)

## 🐳 Quick Start

### 1. Clone or download the project

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

## 🔐 Credentials

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

## 🛑 Stop services

```bash
docker-compose down
```

## 🗑️ Remove everything (including volumes)

```bash
docker-compose down -v
```

**Warning:** This will delete the database data.

## 📁 Estructura de Volúmenes

```
POSTGRES-PGADMIN/
├── postgres/                    # PostgreSQL
│   └── (persistent data base create with for dev development with bind volumes)
├── pgadmin/                     # Config PgAdmin
│   ├── azurecredentialcache/
│   ├── sessions/
│   └── storage/
└── docker-compose.yml           # Config
```

## 🔄 Restart Services 

```bash
docker-compose restart
```

## 📊 logs

```bash
docker-compose logs

# PostgreSQL
docker-compose logs postgres_database

# PgAdmin
docker-compose logs pgadmin_container

docker-compose logs -f
```

## 📚 References

- [PostgreSQL Docs](https://www.postgresql.org/docs/)
- [PgAdmin Docs](https://www.pgadmin.org/docs/)
- [Docker Compose Docs](https://docs.docker.com/compose/)

## � Course Reference

This project was created following the course:

**[Docker - Guía práctica de uso para desarrolladores](https://www.udemy.com/course/docker-kubernetes-curso-completo/)**

By **Fernando Herrera**

It's a lab exercise from the course adapted for learning Docker Compose with PostgreSQL and PgAdmin.

## Learnings
- docker compose files
- networks
- use name volumes