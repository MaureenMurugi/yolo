## Choice of the base image on which to build each container

> Alpine are smaller in size, that consume less disk space

## Dockerfile Directives

> The database service doesn't require additional directives since we're using an official image.
> The Dockerfile for the client service doesn't need custom directives either.
> In the Dockerfile for the backend service, we use WORKDIR to set the working directory, COPY to copy the application code, and RUN to install Node.js dependencies with npm install.

## Docker-compose Networking

> I used a default bridge network for our Docker Compose setup, which allows containers to communicate with each other using their service names as hostnames.

## Docker-compose Volume definition and usage

> For the client and backend services, I did not need volumes since they serve static files or run stateless applications.

## Git Workflow

> Here,