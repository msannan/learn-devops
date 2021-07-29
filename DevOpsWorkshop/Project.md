ARCHIVED - moved to project repo at https://github.com/aliarslan-cs/devops-workshop-project

# Phase-I

You can create any number of microservices you want (2 at least), Better is one of them `should connect to database`. If you are uncomfortable with coding, You can use the code that was presented in the class(Frontend & Backend)
The microservices `each` should have `their own Github` repository.
Phase 1:
The repositories `should contain` the manifests for `docker-compose` of your microservices
For now, you will build and push the docker image to your Dockerhub manually for your code.
If can’t use Database in code, so just add a Database service in docker-compose like Mysql or Mongodb with related environment variables.
So you will have at least 2 repositories based on the number of your microservices:
1. `Backend`: Exposes an API endpoint. This repo will contain the `backend code`, `Dockerfile` to build image, `Docker compose` manifest to deploy it.
2. `Frontend`: Calls the backend and displays the result. This repo will contain the `frontend code`, `Dockerfile` to build image, `Docker compose` manifest to deploy it.

# Phase 2

create pipeline for the services and repos.

Add CI/CD to the above microservices repos. Better to add both Github Actions Workflow and Jenkins but one of them is compulsory…
For a sample golang-app, you can see the Github Actions workflow at
https://github.com/kahootali/golang-sample-app/tree/master/.github/workflows
It will be same for all language apps, only Dockerfile will change…
Github Action to build and push Docker Image
https://github.com/marketplace/actions/build-and-push-docker-images


# Phase 3

will be on Kubernetes, shared after you learn Kubernetes