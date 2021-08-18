Docker

open platform for developing, shipping, and running applications.
separates applications from infrastructure so you can deliver software quickly.
streamlines development lifecycle by allowing developers to work in a standardised environment using local containers.
portability and lightweight nature make it easy to dynamically manage workloads, scaling up or tearing down applications and services as business needs dictate.
A viable, cost-effective alternative to hypervisor-based virtual machines, so you can use more of your compute capacity to achieve your business goals.

provides the ability to package and run an application in a loosely isolated environment called a container.
Run many containers simultaneously on a given host.
lightweight and contain everything needed to run the application.

Example scenario:
* devs write code locally and share work with colleagues using containers
* use docker to push apps into a test environment and execute automated and manual tests
* when bugs found, fix in development environment and redeploy them to the test environment for testing and validation
* when testing is complete, getting the fix to the customer is as simple as pushing the updated image to the production environment.

Uses a client-server architecture. 
Docker client talks to the docker daemon, which does the building, running, and distributing of containers.
They communicate using a REST API.
Docker Compose, lets you work with applications consisting of a set of containers

Images
read-only template with instructions for creating a docker container.
Often an image is based on another image, with some additional customisation.
To build your own image, you create a Dockerfile with a simple syntax for defining steps needed to create the image and run it. 
Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt.
This is part of what makes images so lightweight, small, and fast, when compared to other virtualisation technologies.

Containers
A runnable instance of an image.
You can create, start, stop, move or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

Containers
A runnable instance of an image.
You can create, start, stop, move or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

A container is relatively well isolated from other containers and its host machine. You can control how isolated a container's network, storage, or other underlying subsystems are from other containers or the host.

FROM
WORKDIR
ENV
COPY
RUN
COPY
CMD

# docker best practices
Keep Images Small
* start with appropriate base image
* use multistage builds
* minimise the number of RUN commands in Dockerfile
* if you have multiple images with a lot in common, consider creating your own base image. This way, common layers are loaded once and then cached.
* consider using production image as the base image for the debug image.
* when building images, always tag them with useful tags which codify version information, intended destination, stability, or other information that is useful when deploying the application in different environments.

Where and how to persis application data
* avoid storing data in container's writable layer using storage drivers.
* store data using volumes
* bind mounts - during development, when you may want to mount your source directory or a binary into your container. for production, use a volume instead, mounting it to the same location as you mounted a bind mount during development.
* for production, use secrets to store sensitive application data used by services, and use configs for non-sensitive data such as configuration files.

Use CI/CD for testing and deployment
* When you check in a change or create a pull request, use a CI/CD pipeline to automatically build and tag a Docker image and test it.

Differences in development and production environments
Development | Production
------------------------
Use bind mounts to give your container access to source code | Use volumes to store container data
Use docker desktop for mac or docker desktop for windows | Use docker engine, if possible with userns mapping for greater isolation of Docker processes from host processes.
Don't worry about time drift. | Always run an NTP client on the Docker host and within each container process and sync them all to the same NTP server. If you use swarm services, also ensure that each Docker node syncs its clocks to the same time source as the containers.
