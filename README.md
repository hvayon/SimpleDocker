## **Part 1.Ready-made docker**

- Take the official docker image from nginx and download it using `docker pull`.

	![image info](/part1/docker_pull.png)

- Check for the docker image with `docker images`

	![image info](/part1/docker_image.png)

- Run docker image with `docker run -d 3964ce7b8458`

	![image info](/part1/docker_run.png)

- Check that the image is running with `docker ps`

	![image info](/part1/docker_ps.png)

- View container information with `docker inspect keen_kare`

	![image info](/part1/docker_inspect_1.png)
	![image info](/part1/docker_inspect_2.png)
	![image info](/part1/docker_inspect_3.png)
	![image info](/part1/docker_inspect_4.png)

The container size:\
![image info](/part1/size.png)\
List of mapped ports:\
![image info](/part1/ports.png)\
Container ip:\
![image info](/part1/IPAddress.png)

- Stop docker image with `docker stop keen_kare`

![image info](/part1/docker_stop.png)

- Check that the image has stopped with `docker ps`

![image info](/part1/docker_ps_keen_kare.png)

- Run docker with mapped ports 80 and 443 on the local machine with run command

![image info](/part1/docker_run_name_run-nginx.png)

The **nginx** start page is available in the browser at _localhost:80_

![image info](/part1/nginx.png)

Restart docker container with `docker restart run-nginx`

![image info](/part1/docker_restart_nginx.png)
