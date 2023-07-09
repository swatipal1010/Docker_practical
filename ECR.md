## Amazon ECR
- AWS has its own registry service called "Elastic Container Registry". It's a place to store docker images.
- First create a repository (a private registry). Most of the time we push the images to our private registry sine these images are internal to our application and we don't to share that image with the entire world.
- Every docker image has its own registry. For example, if we have 100 different images then we create 100 different registry where each registry is responsible to store single image.
- If tag immutability is enabled that means if we push an image with a specific tag into the registry, we can't push the same image with different tag into that registry.

![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/078207ca-d1df-4094-a071-ad13e1a38ebe)

- Click on **"View push commands"** option from your AWS registry web console that displays the commands to push an image from our local machine to ECR registry.
- We push our image to ECR registry so that later on we can run it on EC2 instance. We don't manually build the images, Jenkins does this task for us.
- Commands displayed using **"View push commands"** will be performed automatically by the automated server called **JENKINS** when we build pipeline Jenkins server.
- 

