# Nginx deployment for a React app

This project shows how to deploy a pre-created React application using Nginx in a Docker container.

## Project focus

This lab was used to practice:

- serving a React app with Nginx
- understanding the default Nginx configuration inside the container
- building and running a custom image for production-like deployment

## Notes

- Nginx serves static files from the folder `/usr/share/nginx/html`.
- The main configuration file for the default server is `/etc/nginx/conf.d/default.conf`.
- For this project, production dependencies are not needed at runtime because the app is already built and served as static files.

## Steps used

1. Download the pre-created React project.
2. Test Nginx with a basic container:

```bash
docker run --name some-nginx -d -p 8080:80 nginx:1.23.3
```

3. Review the Nginx configuration inside the container:

```bash
/etc/nginx/conf.d/default.conf
```

4. Build the custom image:

```bash
docker build -t heroes-app . --no-cache
```

5. Run the image locally:

```bash
docker container run -p 80:80 heroes-app
```

## Useful commands

```bash
docker run --name some-nginx -d -p 8080:80 nginx:1.23.3
docker build -t heroes-app . --no-cache
docker container run -p 80:80 heroes-app
```

## Notes

- The app is served as static content, so the container only needs Nginx and the built frontend files.
- The Nginx configuration can be modified to match the app routes and deployment needs.
- This is a simple example of deploying a frontend app with Docker and Nginx.