<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

# Teslo API

This project is a NestJS API used as a Docker practice exercise. It was adapted from a precreated project and then configured for local development and production-like workflows.

## Local development setup

1. Clone the project.
2. Install dependencies:
   ```bash
   yarn install
   ```
3. Copy the file `.env.template` and rename it to `.env`.
4. Update the environment variables in `.env`.
5. Start the database:
   ```bash
   docker compose up -d
   ```
6. Start the app:
   ```bash
   yarn start:dev
   ```
7. Run the seed endpoint:
   ```bash
   http://localhost:3000/api/seed
   ```

## Production notes

These notes were kept from the Docker exercise and organized for reference.

- The project was cloned as a precreated base project.
- The README was followed step by step.
- A development stage was added to the Dockerfile.
- The app service was configured with a target in Docker Compose.
- Images can be built with:
  ```bash
  docker compose build
  ```
- Containers can also be run manually with:
  ```bash
  docker container run
  ```
- Update `docker-compose.yml` for dev build with bind volume and app service
- For production, a bind volume is not needed, so a separate file such as `docker-compose.prod.yml` can be used.
- To start the production compose file:
  ```bash
  docker compose -f docker-compose.prod.yml up
  ```
- If only the app service needs to be rebuilt and the database image can be reused, use:
  ```bash
  docker compose -f docker-compose.prod.yml build app
  ```

## Recipe: from simple Compose to production

This project shows how to evolve a basic Docker setup into a more complete production-ready flow.

1. Start with a simple Docker Compose file for local development.
   - The app and database run together.
   - A bind volume can be used to reflect code changes quickly.

2. Improve the Docker image with a multi-stage Dockerfile.
   - One stage is used for development.
   - Another stage is used for production.
   - This keeps the final image smaller and cleaner.

3. Use Docker Compose with a `target` to choose the correct stage.
   - The development stage is useful while coding.
   - The production stage is better for deployment.

4. Create a separate production Compose file.
   - A file such as `docker-compose.prod.yml` can define the final deployment setup.
   - This helps keep local development and production settings organized.

5. For production, avoid bind volumes when they are not needed.
   - The container should use the image built for production.
   - This makes the app more predictable and easier to deploy.

6. Rebuild only what is necessary.
   - If the database image is already valid, rebuild only the app service.
   - Example:
     ```bash
     docker compose -f docker-compose.prod.yml build app
     ```
7. Docker Repository
   - heidyxp/teslo-shop-backend:latest


