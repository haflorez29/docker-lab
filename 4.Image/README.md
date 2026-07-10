# Cron Ticker

This project was created as a learning exercise to understand how to build, run, and publish a Docker image. The process followed the approach from Fernando Herrera's course, with the goal of practicing from creating a simple app to pushing the image to Docker Hub.

## Project goal

- create a basic Node.js app
- add a scheduled task with node-cron
- build a Docker image from the project
- publish the image to Docker Hub
- use Docker Buildx to create images for multiple architectures

## Project structure

- app.js: main app
- package.json: dependencies and scripts
- Dockerfile: Docker image settings
- tests/: basic project tests

## Steps taken

### 1. Initialize the project

```bash
npm init
npm install node-cron
```

### 2. Create the basic app

A simple file was added with a test message and the start script was set in package.json.

```bash
node app.js
```

### 3. Create the Dockerfile

A Dockerfile was added to package the app in a Docker image.

### 4. Build the image locally

```bash
docker build --tag cron-ticker:tag .
```

You can also rename and retag the image:

```bash
docker image tag cron-ticker:latest cron-ticker:1.0.0
```

## Push the image to Docker Hub

### 1. Log in to Docker Hub

```bash
docker login
```

### 2. Create a repository on Docker Hub

A repository was created, then the image was tagged with the repository name.

```bash
docker push heidyxp/cron-ticker:tagname
```

## Run the image

```bash
docker container run -d heidyxp/cron-ticker:tagname
```

## Access the container

```bash
docker exec -it imageId /bin/sh
```

This command lets you enter the container and run commands inside it using the available shell.

## Tests

Jest was added as a development test tool:

```bash
npm i jest --save-dev
```

## Docker Buildx for multiple architectures

Docker Buildx was used to generate images for different architectures.

### 1. Create a builder

```bash
docker buildx create --name container-builder --driver docker-container --bootstrap --use
```

### 2. View available builders

```bash
docker buildx ls
```

### 3. Use the created builder

```bash
docker buildx use container-builder
```

### 4. Build and publish a multi-architecture image

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t heidyxp/cron-ticker:buildx --push .
```

### 5. Stop Builx and back to default

docker buildx use default

### 6. Delete builder

docker buildx rm container-builder

### 7. Logout in to Docker Hub

```bash
docker logout
```

## Final note

This project was practice to understand the full Docker flow: creating the app, preparing the image, testing locally, pushing to Docker Hub, and making versions for several architectures.

Useful reference:
https://docs.docker.com/build/building/multi-platform/#getting-started
