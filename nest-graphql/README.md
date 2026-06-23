# NestJS Todo API with GraphQL

Backend application built with **NestJS** and **GraphQL** to manage tasks (todos). Includes validations, typed DTOs, and a professional modular structure.

## 📋 Description

Complete GraphQL API to manage a task list with the following features:

- **GraphQL API** - Queries and Mutations to manage todos
- **NestJS Modules** - Scalable and maintainable structure
- **Validations** - DTOs with validations using `class-validator`
- **GraphQL Types** - Automatic type definitions
- **Testing** - Configuration for unit and integration tests

## 🚀 Prerequisites

- **Docker** installed
- **Docker Compose** installed
- **Node.js 18.x** (if running without Docker)
- **npm** or **yarn** (if running without Docker)

## 🐳 Running with Docker

### 0. Create network and volume
```bash
- docker network create xxx
- docker network inspect xxxx
- docker volume create volume-name
```

### 1. Run the container manual execute

```bash
docker container run \
--name nest-app \
-w /app \
-p 80:3000 \
-v "$(pwd)":/app \
node:16-alpine3.16 \
sh -c "yarn install && yarn start:dev"
```

The server will be available at: `http://localhost:3000/graphql`

### 2. Stop the container

```bash
docker container stop nest-app
```

### 3. Remove the container

```bash
docker container rm nest-app
```

## 💻 Running without Docker (Local)

### 1. Install dependencies

```bash
npm install
```

### 2. Run in development mode

```bash
npm run start:dev
```

### 3. Run in production

```bash
npm run build
npm run start:prod
```

## 🔗 Access to GraphQL Playground

Once the application is running, access the GraphQL Playground at:

```
http://localhost:3000/graphql
```

### Example Query

```graphql
query {
  getTodos {
    id
    title
    description
    status
  }
}
```

### Example Mutation

```graphql
mutation {
  createTodo(input: {
    title: "My first task"
    description: "Task description"
  }) {
    id
    title
  }
}
```

## 📁 Project Structure

```
src/
├── app.module.ts              # Main module
├── main.ts                    # Application entry point
├── hello-world/               # Hello World Module
│   ├── hello-world.module.ts
│   └── hello-world.resolver.ts
└── todo/                      # Todo Module
    ├── todo.module.ts
    ├── todo.resolver.ts       # GraphQL Resolvers
    ├── todo.service.ts        # Business logic
    ├── dto/
    │   ├── args/
    │   │   └── status.args.ts
    │   └── inputs/
    │       ├── create-todo.input.ts
    │       └── update-todo.input.ts
    ├── entity/
    │   └── todo.entity.ts
    └── types/
        └── aggregations.type.ts
```

## 🧪 Testing

```bash
# Pruebas unitarias
npm run test

# Modo watch
npm run test:watch

# Cobertura
npm run test:cov

# Pruebas e2e
npm run test:e2e
```

## 🛠 Scripts Disponibles

| Script | Descripción |
|--------|-------------|
| `npm run start` | Ejecutar aplicación |
| `npm run start:dev` | Modo desarrollo con watch |
| `npm run start:debug` | Modo debug |
| `npm run start:prod` | Modo producción |
| `npm run build` | Construir aplicación |
| `npm run lint` | Ejecutar linter |
| `npm run format` | Formatear código |

## 📦 Main Dependencies

- **@nestjs/core** - NestJS Framework
- **@nestjs/graphql** - GraphQL Integration
- **@nestjs/apollo** - Apollo Server
- **graphql** - GraphQL Library
- **class-validator** - DTO Validation
- **class-transformer** - Data Transformation

## � Course Reference

This project was created following the course:

**[Docker - Guía práctica de uso para desarrolladores](https://www.udemy.com/course/docker-kubernetes-curso-completo/)**

By **Fernando Herrera**

It's a lab exercise from the course adapted for learning Docker containerization with NestJS and GraphQL.

## Learning
- docker run execution with volume

## �📝 License

MIT
