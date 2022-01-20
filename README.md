**Bitkub Blockchain Technology**

> DevOps Quiz#2 Source Code Template.

---
# Walkthrough

## Technology stacks
* Docker
* Docker-compose
* FluxCD v2
* Github Actions
* k3d

## Dockerize application
### Using Docker
Seperate Dockerfile by each environment as below.
* [`Dockerfile`](/Dockerfile) - for production build
* [`Dockerfile.dev`](/Dockerfile.dev) - for development and local build
```bash
docker build -t $image_name:$imagetag -f $docker_file .
```
### Using Docker-compose
The [`docker-compose.yml`](/docker-compose.yml) consists of the following. </br>
* app (simple app)
```bash
docker-compose up -d
```
### Using Github Actions
The Github Actions consists of following steps. [`(dockerize-and-push.yml)`](/.github/workflows/dockerize-and-push.yml) </br>
1. Check out source code from main branch.
2. Get imagetag from version field in [`package.json`](/package.json).
3. Login dockerhub, build image, and push.
4. FluxCD will do the rest!

## CI/CD Diagram
![Diagram](./images/cicd.png?raw=true "Diagram")