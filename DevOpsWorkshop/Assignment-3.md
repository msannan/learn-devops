# Build the images for Microservices (remember to edit code for frontend) and push images to Dockerhub and send me links for your images… I will run the containers and they should work fine

<https://hub.docker.com/r/aliarsal/frontend-app>

<https://hub.docker.com/r/aliarsal/python-backend>

# How to leverage cache using Dockerfiles

Layers that change more frequently should be placed below layers that change less frequently.

Try to use specific images, for instance, use python image itself as base image instead of using the ubuntu base image and then installing python on it.

# What are multi-stage builds

Multi-stage builds help us optimize our Docker image sizes. For example, we have to containerize an application written in C++. We are only interested in running the applicaiton and not the complicated compiling/building steps involved. We can use a multi-stage build to first create a temporary image which won't be part of the final image, this image installs all the compiling/building tools and builds the application. Then, we can create another image on top of it which just copies the final application.
Only the last stage of the multi-stage build is stored as the image, thus drastically reducing the image size. Multi-stage builds also improve the readibility of the Dockerfile.

# Explain containers vs Image

An image is simply a set of layers, whereas, a container is a running instance of the image. You can have many containers of the same image.

# Explain RUN vs CMD vs Entrypoint
## 1. RUN

It executes a command in a new layer and creates a new image.

## 2. CMD

It sets default command and/or parameters, which can be overwritten from command line when docker container runs.

## 3. Entrypoint

It configures a container that will run as an executable.

Entrypoint can be used to make the container always run a program or executeable when it starts. The parameters - in fact everything - given in CMD is appended to this.
Although CMD can be used for setting the default executeable but its better to use entrypoint for the program/executeable to run at start-up and use CMD for the parameters.


# Improve the Dockerfile for python Application given in slides using the Dockerfile & then improve it and share image size & estimated build time for it

<https://hub.docker.com/r/aliarsal/cached-example-improved>

# Run mysql container using the official image, by persisting data and passing environment variables to set username & password… You can see the information of how to persist and information here

`docker run --name some-mysql -v /home/osboxes/labs/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql`