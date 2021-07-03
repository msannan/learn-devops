# Explain Docker Containers vs VMs

Docker is container based technology and containers are just user space of the operating system. At the low level, a container is just a set of processes that are isolated from the rest of the system, running from a distinct image that provides all files necessary to support the processes. It is built for running applications. In Docker, the containers running share the host OS kernel.

A Virtual Machine, on the other hand, is not based on container technology. They are made up of user space plus kernel space of an operating system. Under VMs, server hardware is virtualized. Each VM has Operating system (OS) & apps. It shares hardware resource from the host.

VMs & Docker – each comes with benefits and demerits. Under a VM environment, each workload needs a complete OS. But with a container environment, multiple workloads can run with 1 OS. The bigger the OS footprint, the more environment benefits from containers. With this, it brings further benefits like Reduced IT management resources, reduced size of snapshots, quicker spinning up apps, reduced & simplified security updates, less code to transfer, migrate and upload workloads.

# Explain Docker Architecture

Docker engine is composed of:
  1. Docker CLI: to perfom action on docker objects using the Daemon via Rest API
  2. Rest API: programs can use to comunicate to Daemon and provide instructions
  3. Docker Daemon: backgroud process that manages images, containers, volumes, and networks


# Write command to create an nginx container in detached mode with name assignment-2 running on host port 9090 on a custom network named assignment-2

    docker network create assignment-2
    docker container run -d --publish 9090:80 --net assignment-2 --name assignment-2 nginx

# Write command to see logs of the above container

`docker container logs assignment-2`

# Write commands to Exec into the container and cat the output of the default nginx file at /usr/share/nginx/html/index.html

`docker container exec -it assignment-2 cat /usr/share/nginx/html/index.html`

# Exit the above container, and now recreate the container by Volume using bind mounting

`docker container run -d -v /home/arsal/assignment-2:/usr/share/nginx/html --publish 9090:80 --net assignment-2 --name assignment-2 nginx`

# Command to exec into the above container and replace the default index.html to a custom one, which says that “I am becoming a Docker Expert” and it should be persisted for the next times

    echo "<html\><head><title>Learn Docker</title></head><body><h1>I am becomming a docker expert</h1></body></html>" > /tmp/index.html
    docker container cp /tmp/index.html assignment-2:/usr/share/nginx/html/index.html