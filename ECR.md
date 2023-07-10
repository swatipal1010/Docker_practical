## Amazon ECR
- AWS has its own registry service called "Elastic Container Registry". It's a place to store docker images.
- First create a repository (a private registry). Most of the time we push the images to our private registry sine these images are internal to our application and we don't to share that image with the entire world.
- Every docker image has its own registry. For example, if we have 100 different images then we create 100 different registry where each registry is responsible to store single image.
- If tag immutability is enabled that means if we push an image with a specific tag into the registry, we can't push the same image with different tag into that registry.

![image](https://github.com/swatipal1010/Docker_practical/assets/110754474/078207ca-d1df-4094-a071-ad13e1a38ebe)

- Click on **"View push commands"** option from your AWS registry web console that displays the commands to push an image from our local machine to ECR registry.
- We push our image to ECR registry so that later on we can run it on EC2 instance. We don't manually build the images, Jenkins does this task for us.
- Commands displayed using **"View push commands"** will be performed automatically by the automated server called **JENKINS** when we build pipeline Jenkins server.
- When we try to communicate to AWS to get login password to our account, AWS stops us and the action fails. We need to provide our identity. We use IAM service(free service) that helps to manage to identity and permissions in the cloud. We create a role and assign policy/policies to it. To create an appropriate role, go to IAM service -> Users -> Search for your username(for shared account) -> Select tour username -> Security credentials -> Access keys -> Create access key -> CLI(selecting access key for CLI because we want to talk with AWS using CLI) -> Next -> Description tag value -> Create access key. At the end of this process we have 2 keys: Access Key and Secret access key. Never commit and push these keys to the github to prevent identity leakage.
- Install aws cli in your local machine as we will communicate to AWS from you local machine using AWS CLI. Execute **"aws configure"** command in your local machine to save the keys generated for your Role in a safe location inside your local machine.
- Now execute the first command from "View push commands" for your ECR registry. It's a command to Retrieve an authentication token and authenticate your Docker client to your registry.
- Then execute second command from "View push commands". Command is to Build your Docker image using the following command. ("docker build -t name_of_the_image"). Don't execute this command if you have already built the image inyour local machine.
- Execute third command so that After the build completes, tag your image so you can push the image to this repository.
- Run the final fourth command to Run the following command to push this image to your newly created AWS repository.


