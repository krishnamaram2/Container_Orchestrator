# Project Title


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

microk8s installation and setup on single node
-----------------------------------------------------
https://thenewstack.io/deploy-a-single-node-kubernetes-instance-in-seconds-with-microk8s/

https://github.com/kubernetes/kubernetes/issues/37922


kubeadm join 172.31.90.236:6443 --token if9pyg.hht3quqm7ln5jzux \
    --discovery-token-ca-cert-hash sha256:a2a9327025443b7fd33174326ccd5b7aa643e75396cc5d36d5e7f680a01f438c 







































































