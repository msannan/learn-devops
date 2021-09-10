# Install docker on ubuntu

The official installation instructions are available [here](https://docs.docker.com/engine/install/ubuntu).

To be on safe side, remove any existing versions of docker. Run:
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

Install using the convenience script
Docker provides a convenience script at get.docker.com to install Docker into development environments quickly and non-interactively. The convenience script is not recommended for production environments, but can be used as an example to create a provisioning script that is tailored to your needs.

Installing docker on ubuntu is as simple as:

    sudo apt install curl
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
