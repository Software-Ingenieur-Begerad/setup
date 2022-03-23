# Deploy Static-gtfs-manager

# Overview

The [project](https://github.com/WRI-Cities/static-GTFS-manager) is to be deployed.

# Preparation

Make sure [docker](docker.md) is installed in development environment and on deployment host.

Build image in development environment.
```
cd
git clone git@github.com:WRI-Cities/static-GTFS-manager.git
cd static-GTFS-manager
docker build -t static-gtfs-manager .
docker images
docker tag static-gtfs-manager:latest danceswithcycles/static-gtfs-manager:march-18-2022
docker images
docker login -u danceswithcycles
docker push danceswithcycles/static-gtfs-manager:march-18-2022
```

# Deployment
