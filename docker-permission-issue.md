# Issue

docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create: dial unix /var/run/docker.sock: connect: permission denied.


If you also face this bug, the following may help you:

1. Create the docker group if it does not exist

    `sudo groupadd docker`

1. Add your user to the docker group.

    `sudo usermod -aG docker $USER`

1. Run the following command or Logout and login again and run (if that doesn't work you may need to reboot your machine first)

    `newgrp docker`

<blockquote>
this will allow you to run docker as non-root user.
</blockquote>
