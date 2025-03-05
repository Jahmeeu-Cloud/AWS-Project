<H1>
☁ Cloud-Based Development: A Beginner's Guide to Building Python Flask Applications with Deployment.☁ 
</H1>

**Getting Started 👨🏽‍💻**

To begin, ensure you have a Linux environment set up. If you're using Windows 10, install Windows Subsystem for Linux (WSL) and configure an instance, as outlined in my previous article.


File Extensions Overview

Familiarize yourself with common file extensions:


🔵 Python: .py
🔵 JavaScript: .js
🔵 C#: .cs
🔵 Ruby: .rb
🔵 PHP: .php


Our Focus

In this tutorial, we'll concentrate on building and deploying Python application, utilizing **.py**



Deployment Guide: Python Application.

## Section A

Create an Instance

Follow the detailed instructions in my previous article to create an instance on AWS EC2: [Post](https://dev.to/jamiu_cloud/how-to-deploy-a-website-on-a-public-domain-with-aws-ec2-39aa)

Refer to Section A for the step-by-step guide 🤓.


## Section B
Connect to Your Server 🤭

Once your instance is set up, connect to your server by following Section B in the same article: [Post](https://dev.to/jamiu_cloud/how-to-deploy-a-website-on-a-public-domain-with-aws-ec2-39aa)



Stay Tuned 😯

For the pictorial deployment guide of Python application.


## Section C

**Deployment Phase** 

Step: Update Virtual Server😌😊.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ujl6foxybr9h1nnln41g.png)



Step 2: Verify Python Installation - Check Version.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ri2qtnv1goz1xvdeolk8.png)


Step 3: Create 'apps' Directory and Verify.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ya4jzjjt06vplpmc3ljg.png)


Step 4: Access 'apps' Folder, Create a New File and Open for Editing.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6eidltpuoe3uah9klvia.png)


Step 5: Add Your Code to the Newly Created File


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vksiqa71wsuieifhbd4h.png)


Step 6: Save & Exit Nano Editor (Ctrl x, Y, Enter)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/islczqx8s88wepti5rge.png)


Step 7: Review File Contents.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3msm6rdh9k0m0szkn8r2.png)


Step 8: Execute Python Code.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n3ylfhs1pb2rj9wphg4y.png)



Step 9: Set Up Virtual Environment. 
(1. You can see it’s not install) (2. You can see it is not install)  (3. Install virtual environment {venv})

Check if Virtual Environment is Installed.

```
python3 -m venv
```

If not installed: 

```
sudo apt-get install python3-venv
```



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qje3ok8vt0iccabmqyw7.png)


Step 10: Run and Activate venv

To activate: 

```
Source Jamiu/bin/activate
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8hgoktir98ctfbqx5zsx.png)


Step 11: Install Flask framework Using pip.


```
pip install flask
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wmlavar6soznmsz40bgd.png)


Step 12: List packages installed in the virtual environment.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8cr5bkykquptb0seeqot.png)



Step 13: Create app.py and Open in Nano Editor.

Insert this code:

```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, This is my first Live Python Flask app!</p>"
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/av3lyo8uwo4w75cu9w7d.png)



Step 14: Execute app.py with Python and Start Flask Server.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w80hutonb1b5lj0bvlqj.png)

Flask app is running, but only accessible internally.


Step 15: Go Live - Make Application Accessible to External Users.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mzmbbdvyat42t7to02uv.png)


Step 16: Verify Application Status - Running and Active.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7eqp8udl0zpkjy9o078t.png)


Congratulations! 🎉 You've Successfully Deployed Your First Flask Application in Python. 🕺🏽🕺🏽🕺🏽



Conclusion:
We've reached the end of this installment. Keep an eye out for my upcoming article, arriving in the next few days😊🙂😌.
