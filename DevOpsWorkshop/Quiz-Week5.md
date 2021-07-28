# What is CI vs CD

CI:

    practice of frequently merging code changes done by developers
    Tools: Jenkins, TravisCI, Bamboo

Continuous Delivery (CD) and Continuous Deployment:

    Continuous Delivery is a practice of continuously maintaining code in a deployable state<br />
    Continuous Deployment is the practice of deploying small code changes to production

# Explain containers vs Image

An image is simply a set of layers, whereas, a container is a running instance of the image. You can have many containers of the same image.

# Container vs VM

Both forms allow multiple operating systems to run on a single physical machine.

With containers, these operating systems are isolated (they have their own file systems, processes, libraries including the libc, IP address, etc.) but they are nevertheless sharing the very same kernel. That's the reason why uname -a showed your host kernel version.

With traditional virtualization, the operating systems have each one their own kernel running. These multiple kernels are not running on top of the real hardware, but on top of a virtualized hardware provided by a piece of software called an hypervisor. This is an extra layer compared to container based virtualization.

Each kind of virtualization has its strenghts and weaknesses. Containers are more limited in the choice of operating systems, the container one must be supported by the running kernel (e.g.: Solaris zones on Solaris, LXC on Linux, WPAR on AIX) although technically, nothing forbid kernel developers to implement the support for "alien" userlands (e.g.: lxbrand = Linux zones on Solaris 10 and SmartOS, or more recently Ubuntu runtime on Windows 10) while with hypervisors, the operating system needs only to be supported by the virtual hardware, which allows much heterogeneous configurations (e.g. : Linux 32 bit and 64 bit kernels, *BSDs, Solaris, Windows, Mac OS X, ...)

The major advantage of containers is they are much lighter, the application performance is essentially the same as what it would be with a true bare metal OS installation. New container instantiation is much faster because there is no extra kernel to boot, and the virtual environment density can be much higher because there are no extra kernels to run.

Note that Docker is not a container implementation. Docker is a building/packaging/distribution standard for applications running in containers and include an engine to run them and recently added an orchestrator too. This engine plays a role similar to the one of an hypervisor, but for applications on containers.

# How to leverage build cache

Layers that change more frequently should be placed below layers that change less frequently.

Try to use specific images, for instance, use python image itself as base image instead of using the ubuntu base image and then installing python on it.

# CMD vs ENTRYPOINT

CMD:

    It sets default command and/or parameters, which can be overwritten from command line when docker container runs.

Entrypoint:

    It configures a container that will run as an executable.

# ARG vs ENV

ENV is mainly meant to provide default values for your future environment variables. Running dockerized applications can access environment variables. It’s a great way to pass configuration values to your project.

ARG values are not available after the image is built. A running container won’t have access to an ARG variable value.

# How to pass an environment variable to Container

    docker run -e var_name

# What are restart policies & How many

Docker provides restart policies to control whether your containers start automatically when they exit, or when Docker restarts. Restart policies ensure that linked containers are started in the correct order. Docker recommends that you use restart policies, and avoid using process managers to start containers.

1. no	Do not automatically restart the container. (the default)
1. on-failure	Restart the container if it exits due to an error, which manifests as a non-zero exit code.
1. always	Always restart the container if it stops. If it is manually stopped, it is restarted only when Docker daemon restarts or the container itself is manually restarted. (See the second bullet listed in restart policy details)
1. unless-stopped	Similar to always, except that when the container is stopped (manually or otherwise), it is not restarted even after Docker daemon restarts.

# Benefits of Docker compose

Docker Compose is used for running multiple containers as a single service. Each of the containers here run in isolation but can interact with each other when required. Docker Compose files are very easy to write in a scripting language called YAML, which is an XML-based language that stands for Yet Another Markup Language. Another great thing about Docker Compose is that users can activate all the services (containers) using a single command.

# Syntax of Docker Compose File

version: '3.7'
services:
    a-service:
        image: redis
        networks:
            - back-end
    b-service:
        build:
            context: ./
            dockerfile: Dockerfile2
        networks:
            - back-end
        environment:
            - Passwort=123    
        ports:
            - 5000:80
        links:
            - s-service
        depends_on:
            - a-service
        volumes:
        - jenkins_home:/var/jenkins_home
networks:
    front-end:
        driver: bridge
    back-end:
volumes:
  jenkins_home:


# Can we build Docker Images at runtime using Docker Compose

yes, see syntax:

    build:
        context: ./
        dockerfile: Dockerfile2

# Benefits of Docker Swarm

Running all your images on a single docker host may not be a good idea for production
environment as we have a single point of failure. Docker Swarm comes in here to resolve
the problem.

With Docker swarm you can combine multiple docker hosts into a single cluster.

It distributes your services into multiple docker hosts for high availability,

Not just high availability, it also help balance the load acros the cluster of Docker hosts,
systems, and hardware.