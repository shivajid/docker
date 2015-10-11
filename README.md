# docker
## Install Docker Binaries

### CentOS 7
The following steps are to setup docker on CentOS 7.


   $ sudo yum update

   $ curl -sSL https://get.docker.com/ | sh

   $ sudo service docker start

   $ sudo docker run hello-world


To create the docker group and add your user:
* Log into Centos as a user with sudo privileges.
* Create the docker group and add your user.
* <code> sudo usermod -aG docker your_username </code>
* Log out and log back in.
* This ensures your user is running with the correct permissions.
* Verify your work by running docker without sudo.
* <code> $ docker run hello-world</code>

Ensure Docker is running as a service

  sudo chkconfig docker on

### Boot2Docker for Mac and Windows
  https://docs.docker.com/mac/step_one/

## Create Docker images 

Use the Dockerfile in the repo to create a CentOS image for HDP Slave Node

<code>
  $ mkdir dockerimage
  $ cp DockerFile dockerimage/
  $ docker build --file=dockerimage/DockerFile ./dockerimage
</code>


+ This will list the newly create image

<code>
  $ docker images 
</code>

+ Tag the image

<code>
  $docker tag shivajid/centos:hdp __imageid__
</code>

+ Create the docker instance. In this command we are opening all the ports. To open a port or a set of ports to teh has

<code>
  $docker run -it -h node0 -P --privileged=true shivajid/centos:centos /bin/bash
</code>


+  User CTRL (P+Q) to exit the container. Do use exit.

+ List all the running containers

  $docker ps

+  Stop a container

  $docker stop __container_name_OR_id

+  Remove a container

  $docker rm __container_name_OR_id

+ To Validate. The container should be gone

  $ docker ps

+  To delete an image. Get the image id from running "docker image"

  $docker rmi __image_id

+  To Validae. Run 

  $ docker image


+  Install Slave Node on the docker images

### Setup the ssh keys

<code>
$service sshd star
$ssh-copy-id root@node0
$ ifconfig

</code>


Update the /etc/host file for the docker container with the ip address mapping for hdpdemo.hortonworks.com

Add an entry for node0 to the host /etc/host file

Use the Ambari wizard to add this host. 
