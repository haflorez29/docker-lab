# Teslo Testing

This project was used to test the Docker image flow for deployment. The goal was to run the app from a built image, connect it to an external database, and push the image to a private registry in DigitalOcean.

## Project focus

This folder is a deployment practice exercise. It shows how to:

- use Docker Compose with a prebuilt image
- connect the app to an external database
- deploy the image to a private registry
- prepare the app for production-like testing

## What I learned

- Docker Compose can be used to run the app from an existing image instead of building everything locally.
- The database service can be commented out when the database is already provided by the cloud environment.
- Environment variables must be updated to use the external database connection.
- A private registry is useful to store and distribute images for deployment.
- Multi-platform builds can be pushed with Docker Buildx.

## Steps used

### 1. Create a Compose file for testing

The Compose file was set up to run the app using the image that had already been created.

```bash
docker compose up --build
```

### 2. Use an external database

The database service in Compose was commented out because the database was already provided in DigitalOcean.

The environment variables were updated to point to the external database.

### 3. Log in to the private registry

```bash
docker login registry.digitalocean.com
```

### 4. Push the image to DigitalOcean Container Registry

```bash
docker buildx build --platform linux/amd64,linux/arm64 -t registry.digitalocean.com/develop-hf-registry/teslo-shop-backend --push .
```

## Notes

- This workflow is useful for testing deployment steps before going to production.
- A private registry helps keep images available for cloud deployment.
- Multi-architecture builds are useful when the app needs to run on different CPU architectures.
