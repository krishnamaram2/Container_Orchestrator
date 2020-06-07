# Project Title

This project implemented to touch and feel of Micro Services architecture with containerized apps

Kubernetes installation and set up with kubeadm
==========================================================


Master



Worker





Step 1: install docker on all machines

https://kubernetes.io/docs/setup/production-environment/container-runtimes/#docker

step 2: install kubeadm,kubecl,kubelet on all machines

https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/

Step 3:KUbeadm initialiazation on matser

kubeadm init

$mkdir -p $HOME/.kube

$sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

$sudo chown $(id -u):$(id -g) $HOME/.kube/config

kubeadm join 172.31.87.27:6443 --token 80lvq0.eirhf8w0cmitbtji \
    --discovery-token-ca-cert-hash sha256:52931c998f27892d68c6bd82525f9d3160c680feb6c699d4bc6f92c25d2a9bb7 

step 4: to make execute commands without root user and then execute below commands on Master node

$mkdir -p $HOME/.kube

$sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

$sudo chown $(id -u):$(id -g) $HOME/.kube/config


Step 5: copy form step3 and run on worker node

kubeadm join 172.31.87.27:6443 --token 80lvq0.eirhf8w0cmitbtji \
    --discovery-token-ca-cert-hash sha256:52931c998f27892d68c6bd82525f9d3160c680feb6c699d4bc6f92c25d2a9bb7 


step 6:choose a network drive for pod network  and execute below command on master node

https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"

step 7: on master

kubectl get nodes -o wide

Kubernetes  installation and setup on single node with microk8s
-----------------------------------------------------------------------
https://thenewstack.io/deploy-a-single-node-kubernetes-instance-in-seconds-with-microk8s/

