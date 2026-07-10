# Multistage Docker Practice

This project was used to learn how to improve a Docker image with multi-stage builds.

## Project focus

This folder shows how to:

- add a `.gitignore` file for cleaner builds
- update a Dockerfile with multiple stages
- build a smaller and more organized production image

## What I learned

- Multi-stage builds help separate the build environment from the final runtime environment.
- The final image can be smaller and cleaner because it only includes what is needed to run the app.
- This approach is useful for production-ready Docker images.

## Steps used

### 1. Add a `.gitignore` file

A `.gitignore` file was added to avoid unnecessary files in the build context.

### 2. Update the Dockerfile with stages

The Dockerfile was modified to use more than one stage:

- one stage for installing dependencies and building the app
- one stage for the final runtime image

### 3. Build the image

```bash
docker build -t heidyxp/cron-ticker:multistage .
```

## Notes

- Multi-stage builds are a common practice in real Docker projects.
- They make the image easier to maintain and more efficient to deploy.
- This is a good step before moving to more advanced production workflows.