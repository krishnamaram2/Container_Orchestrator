# Project Title

This project implemented to touch and feel of Micro Services architecture with containerized apps

Install and set up kubectl
---------------------------

$curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

$chmod +x kubectl

$mv kubectl /usr/bin

# Execution Flow

$git clone https://github.com/krishnamaram2/container-orchestrator.git

$cd container-orchestrator/src/flask

$kubectl create -f flask-deployment.yaml


$cd container-orchestrator/src/mysql

$kubectl create -f mysql-deployment.yaml
