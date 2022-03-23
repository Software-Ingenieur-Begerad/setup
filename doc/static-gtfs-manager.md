# Deploy Static-gtfs-manager

# Overview

The [static-gtfs-manager](https://github.com/WRI-Cities/static-GTFS-manager) project is to be deployed.

# Preparation

Make sure [docker](docker.md) is installed in development environment and on deployment host.

Build image in development environment.
```
cd
git clone git@github.com:WRI-Cities/static-GTFS-manager.git
cd static-GTFS-manager
docker build -t static-gtfs-manager .
docker images
docker tag static-gtfs-manager:latest <user>/static-gtfs-manager:<tag>
docker images
docker login -u <user>
docker push <user>/static-gtfs-manager:<tag>
```

# Deployment
