# Project Title
=>
Docker installation
---------------------------
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
$sudo usermod -aG docker <your-user>


http://discuss.itversity.com/t/setting-up-mesos-cluster-on-redhat-7-or-centos-7/13175
https://developer.ibm.com/technologies/containers/articles/l-mesos-marathon-cluster-on-rhel-little-endian-trs/
https://stackoverflow.com/questions/48496184/marathon-exited-with-status-1
https://open.mesosphere.com/advanced-course/deploying-a-web-app-using-docker/
=>
{
  "id": "/kri",
  "role": "*",
  "cmd": null,
  "cpus": 1,
  "mem": 128,
  "disk": 0,
  "gpus": 0,
  "instances": 1,
  "acceptedResourceRoles": [
    "*"
  ],
  "container": {
    "type": "DOCKER",
    "docker": {
      "forcePullImage": false,
      "image": "tomcat",
      "parameters": [],
      "privileged": false
    },
    "volumes": [],
    "portMappings": [
      {
        "containerPort": 8080,
        "hostPort": 0,
        "labels": {},
        "name": "mysql",
        "protocol": "tcp",
        "servicePort": 10000
      }
    ]
  },
  "networks": [
    {
      "mode": "container/bridge"
    }
  ],
  "maxLaunchDelaySeconds": 300,
  "env": {
    "MESOS_CONTAINERIZERS": "docker,mesos",
    "MESOS_EXECUTOR_REGISTRATION_TIMEOUT": "5mins"
  }
}
=>
Frontend
----------------
FROM centos:7
MAINTAINER "krishnamaram4@gmail.com"
LABEL Purpose=”This is a dockerfile for centos7 and apache httpd server”
RUN yum -y update && yum -y install httpd && yum clean all 
COPY dist /var/www/html
EXPOSE 80
ENTRYPOINT [“ping”]
CMD [“google.com”]


FROM centos
RUN yum install httpd -y
COPY index.html /var/www/html/

CMD [“/usr/sbin/httpd”,” -D”,” FOREGROUND”]
EXPOSE 80

https://linuxtechlab.com/learn-create-dockerfile-example/
https://medium.com/@vi1996ash/steps-to-build-apache-web-server-docker-image-1a2f21504a8e
https://medium.com/@nagarwal/lifecycle-of-docker-container-d2da9f85959


=>https://groups.google.com/forum/#!topic/marathon-framework/b5uPIIwDMek

Log file created at: 2020/03/17 12:05:33
Running on machine: ip-172-31-46-214.ec2.internal
Log line format: [IWEF]mmdd hh:mm:ss.uuuuuu threadid file:line] msg
E0317 12:05:33.041697 10454 slave.cpp:8103] EXIT with status 1: Failed to perform recovery: Collect failed: Failed to run 'docker -H unix:///var/run/docker.sock ps -a': exited with status 1; stderr='Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
'
If recovery failed due to a change in configuration and you want to
keep the current agent id, you might want to change the
`--reconfiguration_policy` flag to a more permissive value.

To restart this agent with a new agent id instead, do as follows:
rm -f /var/lib/mesos/meta/slaves/latest
This ensures that the agent does not recover old live executors.

If you use the Docker containerizer and think that the Docker
daemon state is broken, you can try to clear it. But be careful:
these commands will erase all containers and images from this host,
not just those started by Mesos!
docker kill $(docker ps -q)
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)

Finally, restart the agent.
(END)

=>






































































