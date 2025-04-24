###🚀 How I Deployed My Static Website Using GitHub Actions

Deploying a static website manually can be tedious, especially when you’re updating it frequently. That’s why I decided to automate my deployment process using **GitHub Actions**—a powerful CI/CD tool built right into GitHub.

In this post, I’ll walk you through **how I deployed my static website automatically to an NGINX server using GitHub Actions**.

---

### 🛠️ Tools I Used

- **GitHub** – to store my website’s source code
- **GitHub Actions** – to automate the deployment
- **Ubuntu Server with NGINX** – to host the static site
- **Self-Hosted GitHub Runner** – on the Ubuntu server

---

### 📁 Project Structure

My website files are stored in this directory:
```
_work/ci-static-simple-website/ci-static-simple-website/
│
├── index.html
└── README.md
```

---

### ⚙️ Setting Up the GitHub Action

I created a `.github/workflows/deploy.yml` file in my repo to define the deployment pipeline.

Here’s a simple version of my GitHub Actions workflow:

```yaml
name: Deploy Static Website

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: self-hosted

    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Copy index.html to NGINX Web Directory
      run: |
        cp _work/ci-static-simple-website/ci-static-simple-website/index.html /var/www/html/index.html
        sudo systemctl reload nginx
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j1bji6w6zgix3wgzl6bt.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o68ptpjad30cgrcy5n7a.png)

After successfully testing my code.

---


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5m2n0tluh2dylzyh9ylw.png)

Deploying my code to the Linux self-hosted server in process.

---

### 🔗 How It Works

1. Every time I **push to the `main` branch**, the GitHub Action is triggered.
2. The self-hosted runner on my Ubuntu server picks it up.
3. It copies the `index.html` file into `/var/www/html/`.
4. It reloads NGINX to apply changes immediately.

---

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3fmqffr9wosqme818jcc.png)

Successful deployed and it running fine.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k2kx6pb74hvbgcucrjy6.png)

My Code is running Live.

### 🎉 Final Result

Once the action runs, my static website is instantly live at my server’s public IP!

---

### 💡 Why This Is Awesome

- I **never have to manually copy files again**
- It works perfectly for **personal portfolios**, **landing pages**, or **project demos**
- Super fast and reliable!

---

Let me know in the comments if you'd like a step-by-step guide to setting up your own self-hosted runner or customizing your deployment pipeline!
