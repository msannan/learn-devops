# Install on windows with choco

Open Powershell as admin, and enter these commands:

    Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser

    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

    choco install minikube

run using `minikube start --driver=virtualbox`

## check if it runs successfully

    minikibe status
    kubectl get po -A
    minikube kubectl -- get po -A

