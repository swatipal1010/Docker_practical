## Running container of **"hello-world"** image
- Pull the image from DockerHub using **"docker pull hello-world"** command.
- Run the container of the image using **"docker run hello-world"** command. This container terminates as soon as after its complete execution. If none of the container was running on your local machine before running "hello-world" container and you execute **"docker ps"** command after running this container, you will see none of the active container listed down. To list all the container whether running or stopped can be listed using **"docker ps -a"** command.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/4b520688-8402-4db4-bc76-fb5746059c89)
- To rerun this container use "**docker start <name_of_the_container/orID"** command. To create a new container from the same image use **"docker run hello-world"** command.

## Running Nginx Web Server as a container in the local system using its image **"nginx"** 
- Pull the image from DockerHub using command **"docker pull nginx"**
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/78d75ecc-4f20-4903-a78c-7f57181b6e70)
- Run the container of the image using command **"docker run nginx"**
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/f92468b0-2d9c-40bf-9612-dc9f8bbfa4bd)
- Since every docker container run as a seperate process inside the host machine, we use port mapping to assign a port to the container to communicate with it and then visit the container. Container is listening on port 80 by default (check using DockerHub or "docker ps" command).
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/5d36761d-1358-42cf-877a-beb190b07c79)
- Type **"localhost:3455"** in your browser to see the running container.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/94088563-16a8-484b-9d8a-96581d74e172)
- **"docker run --name mynginx -p 3455:8080 -e NGINX_PORT=8080 nginx"** command is used to name the container as "mynginx" and provide it an environment variable. Using "NGINX_PORT" environment variable we have changed the deafault port of the nginx container from 80 to 8080.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/2a9be05e-02f5-46f6-abe5-c289f15f186f)
- Connect to the container using "localhost:3455" in the browser. To see whether the container is running or not we can either browse to the container or use "docker ps" command.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/199e311c-f684-42b4-b57a-1cbf01dfa1c3)
- To remove the container use **"docker rm <name_of_the_container>"** command.


## Communication Between Two Containers
- Let's run two nginx servers : nginx1 and nginx2.
- Run first container using **"docker run --name nginx1 -p 8080:80 nginx"** command in the terminal.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/06ac5c83-052a-4e10-a423-12aebd339f3b)
- Run second container in another terminal using **"docker run -- name nginx2 -p 8081:80 nginx"** command.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/c1af04bf-513e-4fe6-9c3a-2fc9b1d73245)
- Now consider that we want to communicate with "nginx1" container from "nginx2" container.
- Run **"docker exec -it nginx2 sh"** command to get access to terminal of the running container (in this case : nginx2).
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/bf2da79c-b42e-4b51-bce9-685802cabd98)
- Now we will ping "nginx1" container from "nginx2" container's terminal. Every conatiner has a private IP address that we can know using **"docker inspect <name_of_the_container>"** command.
- To install the ping inside the running container use **"apt install iputils-ping"** command in the container's terminal.
- Now execute **"ping <IP_Address_of_nginx1_container"** command inside the "nginx2" container terminal.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/0fe266d2-01e6-4cba-b5ea-cd24e6ab1a17)
- After executing the ping command we can see that nginx2 contianer is able to communicate with nginx1 container.












