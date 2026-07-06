# Pokemon NestJS App with MongoDB

Backend application to manage a Pokédex using **NestJS** and **MongoDB**. Includes MongoDB, Mongo Express (GUI), and the main application, all orchestrated with Docker Compose.

## 📋 Description

Complete stack that includes:

- **NestJS Application** - Backend framework
- **MongoDB 6.0** - NoSQL database
- **Mongo Express** - Graphical interface to manage MongoDB
- **Docker Compose** - Orchestration of all services
- **MongoDB Authentication** - Database security

## 🚀 Prerequisites

- **Docker** installed
- **Docker Compose** installed (version 3 or higher)

## 🐳 Quick Start

### 1. Clone or download the project

```bash
cd pokemon-app
```

### 2. Create `.env` file

Create a `.env` file in the project root with the following variables:

```env
# MongoDB Configuration
MONGO_DB_NAME=pokemon_db
MONGO_USERNAME=admin
MONGO_PASSWORD=admin123

# Application Configuration
MONGODB=mongodb://admin:admin123@pokemon_db:27017
DB_NAME=pokemon_db
```

### 3. Run Docker Compose

```bash
docker-compose up -d
```

You should see three services:
- `pokemon_db` - MongoDB
- `mongo-express` - Mongo Express (GUI)
- `poke-app` - NestJS Application

## 🔗 Access to Services

### Pokemon Application (API)
- **URL:** `http://localhost:3000`

### Mongo Express (MongoDB GUI)
- **URL:** `http://localhost:8080`
- **Username:** `admin`
- **Password:** `admin123`

## 📊 Services

### MongoDB
- **Port:** 27017 (internal)
- **Username:** admin
- **Password:** admin123
- **Database:** pokemon_db
- **Storage:** Persistent volume `poke-vol`

### Mongo Express
- **Port:** 8080
- **Access:** Automatically connected to MongoDB
- **Function:** Visual database management

### Pokemon NestJS App
- **Port:** 3000
- **Image:** klerith/pokemon-nest-app:1.0.0
- **DB Connection:** Uses container environment variables

## 🛑 Stop services

```bash
docker-compose down
```

## 🗑️ Remove everything (including volumes and data)

```bash
docker-compose down -v
```

## 📁 Structure
```
pokemon-app/
├── docker-compose.yml     # Services configuration
├── .env                   # Environment variables
└── README.md             # This file
```

## 📊 View logs

```bash
docker-compose logs
docker-compose logs poke-app
docker-compose logs db
docker-compose logs mongo-express

# Follow logs in real time
docker-compose logs -f
```

## 🔍 Monitoring

### State in real time
```bash
docker-compose ps -a
```

### Resources
```bash
docker stats
```

## 🔐 Environment Variables

Edit the `.env` file to customize:

```env
MONGO_DB_NAME=pokemon_db              # Database name
MONGO_USERNAME=admin                  # MongoDB username
MONGO_PASSWORD=admin123               # MongoDB password
MONGODB=mongodb://admin:admin123@pokemon_db:27017  # Connection string
DB_NAME=pokemon_db                    # App database
```

## 📚 References

- [NestJS Documentation](https://docs.nestjs.com/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Mongo Express Documentation](https://github.com/mongo-express/mongo-express)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

### Clean up unused resources
```bash
docker system prune
```

## � Course Reference

This project was created following the course:

**[Docker - Guía práctica de uso para desarrolladores](https://www.udemy.com/course/docker-kubernetes-curso-completo/)**

By **Fernando Herrera**

It's a lab exercise from the course adapted for learning Docker Compose orchestration with NestJS and MongoDB.

## Learnings
- enviroments variables
- test mongo connections
- volumes external:false, create a new volume