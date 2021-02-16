# Project Title

This project implemented to touch and feel of Micro Services architecture with containerized apps

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
