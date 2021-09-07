# Install on windows with choco

Open Powershell as admin, and enter these commands:

1. `Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser`

1. `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

1. `choco install minikube`

## run using:

`minikube start --driver=virtualbox`

## check if it runs successfully

    minikube status
    kubectl get po -A
    minikube kubectl -- get po -A

