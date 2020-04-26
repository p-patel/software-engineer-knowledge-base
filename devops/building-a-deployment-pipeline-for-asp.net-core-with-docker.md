# Building a Deployment Pipeline for ASP.NET Core with Docker
https://app.pluralsight.com/courses/c7b61b07-f401-498a-b2bc-38e0e3f72ad2/table-of-contents

## Creating the Pipeline Infrastructure
### Pipeline Overview
- https://app.pluralsight.com/library/courses/docker-images-containers-aspdotnet-core/table-of-contents

### Acessing the Files for the Start of the Course
- fork repo http://github.com/g0t4/aspnetcore-generator-api.git
- clone repo and checkout 'pipeilne-end' branch (the end of the last course)

### Time for CI
- TeamCity (runnng in Docker) with containers used for builds in CI envrionment -> images pushed to (e.g. private or Docker Hub) Docker registry -> registry used to deploy images to host containers

### Creating a Private Registry
- create `/infra/registry/docker-compose.yml` in repo to define CI server infrastructure's Docker registry
- use `registry:2.6.1` image to create a private registry
- add `volumes:` to store images pushed to registry
- map registry port (registry HTTP API published on port 5000)
- spin up registry with `docker-compose up -d`
- `docker-compose` configures a default network

### Aliasing the Private Registry in /etc/hosts
- add alias to hosts file for easier navigation to registry host (e.g. http://my-registry:55000/v2/_catalog)

### Pushing an Image to the Private Registry
- in non-dev environments, secure the registry with username/password and SSL
- for local (unsecure) purposes: Docker for Windows | Daemon | add unsecure registry address (requires restart of Docker for Windows)
- update registry's docker-compose.yml file to auto-restart service (in case of Docker host restart as above)
- `docker build -t a\b .`
- `docker tag a\b my-registry\a\b`
- `docker push my-registry\a\b http://my-registry:55000`

### Creating a TeamCity cluster with docker-compose
- add teamcity server and teamcity agent images to `/infra/teamcity/docker-compose.yml`
- set data volumes for teamcity server to use
- TC agent needs volume `/var/run/docker.sock:/var/run/docker.sock (to be able to run docker images)
- stand up cluster with `docker-compose up -d`

### TeamCity Setup
- run and complete TC setup
- select db (inc. containerised db)
- create TC admin account
- authorise the TC agent
- process can be adapted to easily stand up any CI server environment

## Creating a CI Dockerfile with Unit Tests
### Big Picture Intro
- 



