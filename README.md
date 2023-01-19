## **Part 1. Ready-made docker**

- Take the official docker image from nginx and download it using `docker pull`

	![image info](/img/part1/docker_pull.png)

- Check for the docker image with `docker images`

	![image info](/img/part1/docker_image.png)

- Run docker image with `docker run -d 3964ce7b8458`

	![image info](/img/part1/docker_run.png)

- Check that the image is running with `docker ps`

	![image info](/img/part1/docker_ps.png)

- View container information with `docker inspect keen_kare`

	![image info](/img/part1/docker_inspect_1.png)
	![image info](/img/part1/docker_inspect_2.png)
	![image info](/img/part1/docker_inspect_3.png)
	![image info](/img/part1/docker_inspect_4.png)

The container size:\
![image info](/img/part1/size.png)\
List of mapped ports:\
![image info](/img/part1/ports.png)\
Container ip:\
![image info](/img/part1/IPAddress.png)

- Stop docker image with `docker stop keen_kare`

![image info](/img/part1/docker_stop.png)

- Check that the image has stopped with `docker ps`

![image info](/img/part1/docker_ps_keen_kare.png)

- Run docker with mapped ports 80 and 443 on the local machine with run command

![image info](/img/part1/docker_run_name_run-nginx.png)

The **nginx** start page is available in the browser at _localhost:80_

![image info](/img/part1/nginx.png)

- Restart docker container with `docker restart run-nginx`

![image info](/img/part1/docker_restart_nginx.png)

## **Part 2. Operations with container**

 - Read the *nginx.conf* configuration file inside the docker container with the *exec* command

![image info](/img/part2/docker_exec.png)

- Create a *nginx.conf* file on a local machine

![image info](/img/part2/touch_nginx.png)

- Configure it on the */status* path to return the **nginx** server status page

![image info](/img/part2/my_nginx_file.png)

- Copy the created *nginx.conf* file inside the docker image using the docker `cp command`

![image info](/img/part2/docker_cp.png)

- Restart **nginx** inside the docker image with exec

![image info](/img/part2/docker_exec_2.png)

- Check that *localhost:80/status* returns the **nginx** server status page

![image info](/img/part2/localhost_status.png)

- Export the container to a *container.tar* file with the *export* command

![image info](/img/part2/export.png)

- Stop the container

![image info](/img/part2/docker_stop_run_nginx.png)

- Delete the image with `docker rmi [image_id|repository]` without removing the container first

![image info](/img/part2/docker_rmi_3.png)

- Delete stopped container

![image info](/img/part2/docker_rm_run-nginx.png)

- Import the container back using the *import* command

![image info](/img/part2/docker_import_cmd.png)

- Run the imported container

![image info](/img/part2/docker_run_80.png)

- Check that *localhost:80/status* returns the **nginx** server status page

![image info](/img/part2/localhost80:80.png)

## **Part 3. Mini web server**

- Write a mini server in **C** and **FastCgi** that will return a simple page saying **Hello World!**

`docker pull nginx` - download nginx image  
`docker images` - check image id  
`docker run -d -p 81:81 *IMAGE_ID*` - run docker with mapped ports  

![image info](/img/part3/docker_pull_nginx.png)

Place the mini web server file in the directory

![image info](/img/part3/docker_cp_main.png)

`main.c` file content

![image info](/img/part3/cat_main.png)

- Run the written mini server via spawn-fcgi on port 8080

Updating the container. Installation gcc, spawn-dcgi, libfcgi-dev

![image info](/img/part3/update_container.png)

Compiling and running our server

![image info](/img/part3/run_serv.png)

- Write your own nginx.conf that will proxy all requests from port 81 to 127.0.0.1:8080

![image info](/img/part3/own_nginx.png)

- Check that browser on localhost:81 returns the page you wrote

Reloading the container and checking the page in the browser  

![image info](/img/part3/localhost:81.png)
![image info](/img/part3/localhost_browser.png)

- Put the nginx.conf file under ./nginx/nginx.conf (you will need this later)

![image info](/img/part3/nginx_file.png)

## **Part 4. Your own docker**

- Creating a docker image

![image info](/part4/img/docker_image.png)

- Running a script from docker

![image info](/part4/img/docker_script.png)

- Build the written docker image with `docker build`, specifying the name and tag

![image info](/part4/img/docker_build.png)

- Check with `docker images` that everything is built correctly

![image info](/part4/img/docker_images.png)

- Run the built docker image by mapping port 81 to 80 on the local machine and mapping the *./nginx* folder inside the container to the address where the nginx configuration files are located

![image info](/part4/img/docker_run.png)

- Check that the page of the written mini server is available on localhost:80

![image info](/part4/img/curl_localhost:80.png)

- Add proxying of */status* page in *./nginx/nginx.conf* to return the **nginx** server status

![image info](/part4/img/nginx_file.png)

- Restart docker image

![image info](/part4/img/docker_restart.png)

- Check that *localhost:80/status* now returns a page with **nginx** status

![image info](/part4/img/curl_localhost:80:status.png)

## **Part 5. Dockle**

- Check the image from the previous task with dockle `[image_id|repository]`

![image info](/part5/img/install_dockle.png)

![image info](/part5/img/check_dockle_1.png)

![image info](/part5/img/check_dockle_2.png)

- Fix the image so that there are no errors or warnings when checking with **dockle**

![image info](/part5/img/dockerfile.png)

![image info](/part5/img/docker_build_new.png)

![image info](/part5/img/docker_run_new.png)

![image info](/part5/img/check_dockle_new.png)

![image info](/part5/img/docker_localhost.png)

## **Part 6. Basic Docker Compose**

- Write a docker-compose.yml file, using which:

1) Start the docker container from Part 5 (it must work on local network, i.e., you don't need to use EXPOSE instruction and map ports to local machine)


2) Start the docker container with nginx which will proxy all requests from port 8080 to port 81 of the first container

![image info](/part6/img/docker-compose.png)

- Map port 8080 of the second container to port 80 of the local machine

- Stop all running containers

![image info](/part6/img/docker_ps.png)

- Build and run the project with the `docker-compose build` and `docker-compose up` commands

![image info](/part6/img/docker-compose_build.png)

![image info](/part6/img/docker_images.png)

![image info](/part6/img/docker-compose_up.png)

- Check that the browser returns the page you wrote on localhost:80 as before

![image info](/part6/img/check_work.png)





