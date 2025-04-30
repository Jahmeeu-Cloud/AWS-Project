_🚀 How I Achieved My Project: Deploying Docker Images to Amazon Elastic Container Registry (ECR)🐳_


In this post, I’ll walk you through how I successfully pushed my Docker image to **Amazon Elastic Container Registry (ECR)** and how Docker made the whole process incredibly seamless. This project involved leveraging Docker's simplicity to move an image from **Docker Hub** to **AWS ECR** and then deploying it onto an EC2 instance. Here’s how I did it.

How Docker Streamlined the Project
Docker revolutionizes application deployment by allowing developers to package their applications and all dependencies into containers, ensuring portability and consistency across environments. One of the key benefits of Docker is its ability to create reproducible environments, which makes deploying applications easier and more reliable.

For this project, I used Docker to build my image and initially pushed it to Docker Hub. When it was time to transfer the image to AWS ECR, Docker’s straightforward commands allowed me to easily pull and push the image to ECR, making the process seamless.

## **Steps to Achieve the Project**

### **1. Docker Installation and Setup**

Before starting, I made sure that **Docker** and **AWS CLI** were installed on my system. Here are the basic commands to get Docker running on an Ubuntu system:

#### Install Docker on Ubuntu:
```bash
sudo apt update
sudo apt install docker.io
```

or 

Check my previous post i.e [Part 1](https://dev.to/jamiu_cloud/getting-started-with-docker-from-installation-to-pushing-images-to-docker-hub-4of6)

#### Install AWS CLI:
```bash
sudo apt install awscli
```

or 

Follow this official document [code](https://docs.aws.amazon.com/AmazonECR/latest/userguide/getting-started-cli.html)

Once installed, I configured the AWS CLI using the following command:
```bash
aws configure
```
This allows you to set your AWS access key, secret access key, and default region.

---

### **2. Authenticate Docker to AWS ECR**
Since my goal was to move the Docker image to AWS ECR, the next step was to authenticate Docker to AWS using the AWS CLI. The **get-login-password** command simplifies this process by securely logging Docker into ECR.

Authenticate Docker to ECR:

#### Authenticate Docker to ECR:
```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 9111****75.dkr.ecr.us-east-1.amazonaws.com
```

This command retrieves the authentication token from AWS and logs Docker into the specified ECR repository.

---

### **3. Docker Image Build and Push to Docker Hub**
For this project, I started by pulling my image from Docker Hub. Once the image was pulled, I ran the container using the following command:

Pull the Docker Image:

#### Pull the Docker Image:

```bash
docker pull horlacloud/webapp
```

This command pulls the Docker image from Docker Hub.

After pulling the image, I proceeded to push the container to AWS ECR so that it could be pulled from there later.


### **4. Tag the Docker Image for ECR**
With Docker authenticated to ECR, I tagged my image to point to the correct repository in AWS ECR. The following command tags the image with the appropriate ECR repository URI:

#### Tag Docker Image:

```bash
docker tag webapp:latest 9111****75.dkr.ecr.us-east-1.amazonaws.com/webapp:latest
```

This step prepares the image for pushing to ECR.

---

### **5. Push the Image to ECR**

After tagging the image, I pushed it to the AWS ECR repository using the command below:

#### Push Image to ECR:

```bash
docker push 9111****75.dkr.ecr.us-east-1.amazonaws.com/webapp:latest
```

This command uploads the image to the Amazon ECR repository, making it available for further deployment.

---

### **6. Running Docker Image on EC2**

To run the image on an EC2 instance, I executed the following commands. This involved pulling the image from ECR and running it on the instance.

#### Run the Docker Container:
```bash
docker run -d -p 8080:80 9111***75.dkr.ecr.us-east-1.amazonaws.com/webapp:latest
4f04c29bffc5929f40306b0edd282464a9e23bdf5c24f42c1abdb4c84ea84043
```

After executing the above command, my application was running on port 8080 on the EC2 instance. To access the application, I simply visited:

```
http://<ec2-public-ip>:8080
```

---

## **Useful Docker Commands for the Project**

Here are a few **helpful Docker commands** I used throughout the process:

### **Making the `ubuntu` user a root user**  
If you want to add the `ubuntu` user to the Docker group (so it can run Docker commands without `sudo`), use:

```bash
sudo usermod -aG docker ubuntu
```

Then, log out and log back in for the changes to take effect.

### **Check Docker Images**  
To see the list of images on your system, run:
```bash
docker image ls
```

### **Removing Docker Images**  
If you need to remove an image, use:
```bash
docker rmi <image-id>
```

If a container is using the image, stop and remove the container first with:
```bash
docker stop <container-id>
docker rm <container-id>
```

### **View Running Containers**  
To list all running containers:
```bash
docker ps
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/f0gfimkmqzzaojol97ew.png)



---

## **Conclusion**

Docker has significantly streamlined the process of moving containerized applications between environments. By pushing my Docker image to Docker Hub and pulling it into AWS ECR, I was able to quickly deploy my application on an EC2 instance with minimal configuration. Docker’s portability and ease of use make it an invaluable tool for cloud-native application deployments.

With AWS ECR and Docker, I now have a robust and scalable containerization pipeline ready for future projects. Docker's simplicity makes managing and deploying applications easier and more efficient than ever.
