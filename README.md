# Project Title


Kubernetes installation and set up with kubeadm
==========================================================
Step 1: install docker on all machines
https://kubernetes.io/docs/setup/production-environment/container-runtimes/#docker

step 2: install kubeadm,kubecl,kubelet on all machines
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/

Step 3:KUbeadm initialiazation on matser
kubeadm init
mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config


kubeadm join 172.31.87.27:6443 --token 80lvq0.eirhf8w0cmitbtji \
    --discovery-token-ca-cert-hash sha256:52931c998f27892d68c6bd82525f9d3160c680feb6c699d4bc6f92c25d2a9bb7 

step 4: to make execute commands without root user and then execute below commands on Master node
mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config


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




https://www.youtube.com/watch?v=QRyZdfZV0mU

docker run -d -p 2181:2181 --name zookeeper zookeeper:3.4.11




docker run -dit --name mesos-master1 -p 5050:5050 --link zookeeper -e MESOS_ZK=zk://zookeeper:2181/mesos -e MESOS_QUORUM=1 -e MESOS_CLUSTER=docker-compose -e MESOS_HOSTNAME=localhost -e MESOS_WORK_DIR=/var/tmp/mesos -e MESOS_LOG_DIR=/var/log/mesos mesosphere/mesos-master:1.4.1




docker run -dit --name mesos-slave6 -p 5051:5051 --link zookeeper:zookeeper --link mesos-master1:mesos-master1 -e MESOS_MASTER=zk://localhost:2181/mesos -e MESOS_CONTAINERIZERS=docker  -e MESOS_PORT=5051 -e MESOS_RESOURCES=ports:[11000-11999] -e MESOS_HDDDOSTNAME=localhost -e MESOS_WORK_DIR=/var/tmp/mesos -e MESOS_LOG_DIR=/var/log/mesos -e MESOS_SYSTEMD_ENABLE_SUPPORT="false" --volume=/var/run/dockerDDD.sock:/var/run/docker.sock  mesosphere/mesos-slave:1.4.1


docker run -dit --name marathon1 -p 8080:8080 --link zookeeper:zookeeper --link mesos-master1:mesos-master1 -e MARATHON_ZK=zk://localhost:2181/marathon  -e MESOS_MASTER=zk://localhost:2181/mesos mesosphere/marathon:v1.5.6























docker run -it --entrypoint=/bin/bash mesosphere/marathon -s


This project is used to Archestrate conatainers 


https://linuxacademy.com/guide/28039-container-orchestration-using-mesos-and-marathon/

https://www.digitalocean.com/community/tutorials/an-introduction-to-mesosphere

Installation and set up
========================


Mesos-master
http://mesos.apache.org/documentation/latest/binary-packages/



Mesos-slave



Marathon
https://mesosphere.github.io/marathon/docs/


Zookeeper
https://wpcademy.com/how-to-install-apache-zookeeper-on-centos-7/
https://zookeeper.apache.org/releases.html#download
https://zookeeper.apache.org/doc/r3.6.0/zookeeperStarted.html#sc_Download















Mesos + marathon + zookeeper installation and set up on single node
----------------------------------------------------------------------
http://www.swisspush.org/clustering/2014/12/05/install-mesos-on-singlenode
https://www.digitalocean.com/community/tutorials/how-to-configure-a-production-ready-mesosphere-cluster-on-ubuntu-14-04


https://github.com/kubernetes/kubernetes/issues/37922


kubeadm join 172.31.90.236:6443 --token if9pyg.hht3quqm7ln5jzux \
    --discovery-token-ca-cert-hash sha256:a2a9327025443b7fd33174326ccd5b7aa643e75396cc5d36d5e7f680a01f438c 







































































