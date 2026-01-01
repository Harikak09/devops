## Project Overview

A basic web app using flask, containerized with Docker deployed to Kubernetes, with infrastructure created using CI/CD using Github Actions


### Flow:

Web App -> runs inside docker

Kubernetes cluster -> runs container

Github Actions -> automates build and deploy for docker images

*Step 1: Building web app*

*Step 2: Dockerize the app*

- Build the image:
    `docker build image -t <image_name:tag>`

- Containerize the image
    `docker container run --detach --rm --name <name> --publish 8888:80 <image_name:tag>`

map host 8888 → container 80

Accessing locally at localhost:8888

- Tag the image for Docker Hub 
    `docker tag <image_name:tag> <your-username/image_name:tag>`

- Push the image
    `docker push <your-username/image_name:tag>`


*Step 3: Kubernetes*

- Add deployment and services yaml files

    `kubectl apply -f k8s-deployment.yaml`

    `kubectl apply -f k8s-service.yaml`

- Flow of traffic: Browser -> Node Port -> Service -> Pods -> Container


*Step 4: CI/CD with Github Actions*

- Gets trigger on push to main branch