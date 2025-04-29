###🚀 Getting Started with Docker: From Installation to Pushing Images to Docker Hub

If you're new to Docker or looking for a simple guide to go from setup to publishing your containerized app, this post is for you. In this tutorial, you'll learn how to:

- Install Docker on Ubuntu  
- Build your first Docker image  
- Create and run a container  
- Tag and push your image to Docker Hub  

Let’s get started.

---

### 🐳 Step 1: Install Docker on Ubuntu

Open your terminal and run the following commands:

```bash
sudo apt update
sudo apt install -y docker.io
```

🔗 **Alternative method:**  
For the latest version and installation options, check the official Docker install script:  
{% embed https://get.docker.com/ %}

To verify Docker is installed correctly:

```bash
docker --version
```
or  

```bash
docker -v
```

---

### 📂 Useful Docker Commands

- **List Docker images**:
```bash
docker image ls
```

- **List Docker containers**:
```bash
docker container ls
```

---

### 🛠 Step 2: Build Your Docker Image

Let’s use a static website as an example, such as one downloaded from [startbootstrap.com](https://startbootstrap.com).

1. Create a `Dockerfile` in your project directory:

```bash
nano Dockerfile
```

2. Add the following content:

```Dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
```

3. Build the Docker image:

```bash
docker build -t webapp:v1 .
```

To confirm the image was created:

```bash
docker image ls
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0xeuxeq366wcfm1e0jda.jpeg)



---

### 🚀 Step 3: Run the Container

Now let’s run your image in a Docker container:

```bash
docker run -d -p 80:80 --name websiteapp webapp:v1
```

Visit `http://localhost:80` (or your server’s public IP) to see your site live.

To list running containers:

```bash
docker container ps
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bscfysw580ytcmw5bq39.png)

---

### 🔐 Step 4: Log in to Docker Hub

If you don’t have a Docker Hub account, [sign up here](https://hub.docker.com/).

Then log in from your terminal:

```bash
docker login -u your_dockerhub_username
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/twy298d54qk1n6t6xw0r.png)


> You’ll be asked to enter your password or a [Personal Access Token (PAT)](https://hub.docker.com/settings/security).

---

### 📦 Step 5: Tag & Push Your Image to Docker Hub

1. Tag the image:

```bash
docker tag webapp:v1 your_dockerhub_username/webapp:v1
```

2. Push the image:

```bash
docker push your_dockerhub_username/webapp:v1
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dku5d015m1p2o90mnyah.png)



You can now visit your Docker Hub profile and view your pushed image:  
👉 [https://hub.docker.com/repositories](https://hub.docker.com/repositories)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qizyljrirdqmdf39k26m.jpeg)

---

After Successful Push


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/61qn0xhk0tm9kt63e6qf.jpeg)



---

### ✅ Summary

In this guide, you learned how to:

- Install Docker on Ubuntu  
- Build and run a Docker image  
- Host a simple static site using NGINX  
- Push your Docker image to Docker Hub  

This workflow forms the backbone of containerized development. You can now use these skills to automate deployments, integrate with CI/CD pipelines, or scale with orchestration tools like Kubernetes.

---

💬 **Have questions or want to learn how to automate deployment using GitHub Actions or AWS ECS? Leave a comment or reach out — I’d love to help!**

