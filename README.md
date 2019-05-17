## Linux Distro Testing
Docker-based images used for cross-platform testing. This is a quick way to startup multiple, container-based distros. It is useful when testing cross-platform compatibility.

* Supported distros (currently using latest versions)
	* Alpine
	* CentOS
	* Ubuntu

* To start the environments
	1. Start the Docker engine
	2. cd to **docker**
	3. execute

			docker-compose up -d	
* To access the distro shells,
	1. Get the distro container information

			docker container ls
	2. "exec" to the distro container command line [^1]

			docker exec -it <container name> /bin/sh
* To exit the the container shell

			exit
* To stop and remove the distro containers and associated docker network

		docker-compose down
* To shut down and remove any volumes that may have been created

		docker-compose down --volumes
* To shut down and remove all the distro images [^2]

		docker-compose down --rmi all


[^1]: Not using the [attach](https://docs.docker.com/engine/reference/commandline/attach/) command because exiting from the shell will detach and stop the container, which may not be the desired behavior during testing.

[^2]: Refer to the [docker-compose down documentation](https://docs.docker.com/compose/reference/down/) for details on the images to be removed. An alternative method is to remove each of the images with `docker image rm <image id>`


