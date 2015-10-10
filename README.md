# docker
The following steps are to setup docker on CentOS 7.
<code>

$ sudo yum update

$ curl -sSL https://get.docker.com/ | sh

$ sudo service docker start

$ sudo docker run hello-world

</code>

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
