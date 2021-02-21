# Project Title

This project implemented to touch and feel of Micro Services architecture with containerized apps

Install and set up kubectl
---------------------------

$curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

$chmod +x kubectl

$mv kubectl /usr/bin

# Execution Flow

$git clone https://github.com/krishnamaram2/container-orchestrator.git

$cd container-orchestrator/src/mysql

$kubectl create -f mysql-pod.yml

$kubectl create -f mysql-svc.yml

$kubectl create -f mysql-deploy.yml

$cd container-orchestrator/src/flask

$kubectl create -f flask-pod.yml

$kubectl create -f flask-svc.yml

$kubectl create -f flask-deploy.yml



to list containers in flask pod

kubectl describe pod/flask-pod

to login to flask container

kubectl exec -it flask-pod --container flask -- /bin/bash



to list containers in  mysql pod

kubectl describe pod/mysql-pod

to login to mysql container

kubectl exec -it mysql-pod --container mysql -- /bin/bash

