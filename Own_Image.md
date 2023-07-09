## Creating my own image of simple_flask_webserver
- Specify the neccessary steps in the Dockerfile.
- Move to the directory that conatins all the code and Dockerfile required to create an image.
- Execute **"docker build -t my_flask_app:0.0.1 ."** command in the terminal where -t is used to give tag to the image and . is the build context specifying to docker that the "current working directory", is the build context.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/57e026cf-c117-4286-8239-ac3a1fc609d0)
- We can change the version of the image by changing its tag. Now, if we run the **"docker build -t my_flask_app:1.2 ."** command in the terminal and if no changes are made to the Dockerfile, image will be built using cached layers of the previously built image.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/2ae0087f-d298-4db8-81b4-071b6d01ed76)
- To run the image locally in the host image, execute **"docker run -p 8080:8080 my_flask_app:1.2"** command in the terminal.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/a7bbbb7c-311a-47b7-8fa8-9578175aa630)
- To communicate with the image, type **"localhost:8080"** in the browser since container listens on port 8080.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/7c71e4f7-b340-43cb-93b6-f30ab246f171)

- Execute **"docker inspect my_flask_app:1.2"** command to ge the details about the image like the number of layers it is composed of.
![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/19be6a50-9f83-41c5-a1a2-11712e878f1a)





 
