## The wait is over! Welcome to Week 4.

Congratulations! 🎉 I just crossed the halfway mark of this bootcamp 🤩🎊🍾🎁🥳🎉

> Case Study: Deploying a Website
> A client needs to deploy their website or blog on a public domain, making it easily accessible worldwide via a shared URL. Let's dive into the solution together.


**Overview:**
Let's get started!
Let's Dive in as we explore the solution together. We'll cover:

- Deploying a website on a public domain using EC2
- Step-by-step guide
- Understanding EC2's features and benefits
- Graphical illustrations
- Hands-on steps to resolve the case study

**Solution** 
Introducing EC2: Elastic Cloud Compute
To solve this problem, we'll utilize Amazon Web Services (AWS) popular service: EC2 (**E**lastic **C**loud **C**ompute). But what is EC2? 🤔


EC2 provides scalable computing capacity in the cloud, allowing users to run and manage applications seamlessly.



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7w52absxm44auwyee3mw.png)




Why **EC2**? **EC2** is a popular choice for many reasons in terms of the following:

**Scalability:** Quickly scale up or down to match changing workloads and applications.

**Flexibility:** Choose from a wide range of instance types, operating systems, and configurations.

**Reliability:** Enjoy high uptime and reliability, with built-in redundancy and failover capabilities.

**Security:** Leverage robust security features, including network isolation, firewalls, and encryption.

**Cost-effectiveness:** Pay only for the resources you use, with no upfront costs or long-term commitments.

**Integration:** Seamlessly integrate with other AWS services, such as storage, databases, and analytics.

**Global reach:** Deploy applications in multiple regions and availability zones, with low latency and high performance.

**Automation:** Easily automate tasks and workflows using AWS tools and services.

**Support:** Access comprehensive documentation, tutorials, and support from AWS and the community.

In summary: **EC2** should give me a virtual machine on your cloud platform (**AWS**) which is elastic in nature.



Let’s dive with graphical illustrations:

##<u>Section A</u> 

Step 1: Open your AWS management console.
  

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9kkslbtceijaowolfzlo.png)


Step 2: Locate EC2.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/39p1aw84nui88riwv1fc.png)



Step 3: Give your server a server.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/a852re0fv2yra0vnu3od.png)


Step 4: Select AMI and instance type

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hqkki9ygs3z3cgqo6xw6.png)

Step 5: Create and type the name key. 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n7egh2wdy4wyohusy5i9.png)

**Congratulation!**, You have created your first instance.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/avm04w4g3i689owz1h77.png)



##<u>Section B</u> 
Now, let’s deploy our server. Steps to deploy server.

Step 1: Click on Connect, and it prompt this page to connect to our server.  Select SSH client.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ecpd9q5yzqs4c6nxchvi.png)


Step 2:  Open your Gitbash (open SSH client).


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b1o3gq4ctutgxh6ld3ow.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ocbw983f0fb2w6ji7fal.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j842gxqw0i961k8ch0a5.png)


Step 3: Make sure your directory is located at where your key and run the command line.

```
chmod 400 "cloud-jay-key.pem"
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k6kbhaiydmcp9bezmnql.png)

Step 4: run the second command line and it request your permission: **Yes** / **No** click on **Yes** to continue



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fx9z6uyua6hb09v84cvg.png)

When you type yes. It shows this


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/d7javbkpnt1egbwbs460.png)




![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nld0aw9tzhqmirlb1ez6.png)


Step 5: run this command line:

```
ssh -i "cloud-jay-key.pem" ec2-user@ec2-34-204-186-40.compute-1.amazonaws.com

```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1qkc04cfbnbpscu1tkmt.png)



Step 6: check the updated version.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3pulj5tsbqjv0ssjdswo.png)



Step 7: install nginx, prompt yes or now. Click “yes” to install

Before installation of nginx	 **==>**    after installation of nginx	



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/na80rveger8487bxgkkd.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yzkbj00k5bv1bd56k1ir.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fqsqnpbvdyz7uq7ww13a.png)


Step 8: checking the version of nginx


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/o2wybam9gzwz0p6lwgx2.png)


Step 9: Test if the nginx is running.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wz54n7adde8sqq6sd7gd.png)

Step 10: set up inbound rules


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pkss8kj7srflude7fzth.png)


Step 11: click on security rules then click on edit inbound rules


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mrv57m8gegmvn4kpp69x.png)


Step 12: select the option in sequence. 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/14sd2qybp8ajpph14fch.png)


Step 13: now inbound rules in set.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x3hlydq3bz6adjuim27e.png)


Step 14: Test if the localhost is running.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7dge3ns5rvbkoww44len.png)


Step 15: Check the status the nginx (it shows the status is disable)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c18fszhl8javdtug6re4.png)


Step 16: Start enable nginx and check the status if it enables or running.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cnyr8jnpnf78a19rcm7b.png)

Step 17: Let’s confirm if nginx is running on web browser. (copy public IP address and run it on browser: e.g [google chrome, opera, Mozilla, Brave etc.]).


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cbn7fhs54zhc84b243uc.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1t184g90ewr97o40h93t.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5kbm88g4nfcpjs3f2vgv.png)


**Congratulation!**, Nginx is running on web browser.


Steps to setup an nginx webserver:


1. Create the ec2 instance - amazon linux.
2. Connect via ssh using the key on git bash
3. Update the instance using (sudo yum update)
4. Install the nginx package (sudo yum install nginx)
5. Check if installed (nginx –v)
6. Test using (curl localhost)
7. Check if nginx is running (sudo systemctl status nginx)
8. Start nginx using (sudo systemctl start nginx)
9. Check the status again using step 7
10. Test using the public IP.
11. Check and allow traffic on your security group by adding http port 80 rule on IPv4.



## <u>Section C</u>

Step Let’s deploy our blogspot on nginx as client requested.
Sample of the website deploy.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/e3k8d0uoid7y233dbg4v.png)


Step 1: We are using a readymade blogspot to deploy our first website for the client. Right click and copy link address.



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mpcm9zqex7vgqkc8micp.png)


Step 2: Enter the dir of nginx html (cd /usr/share/nginx/html) and ls


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/daf5ym0ox4rguo4bp0v3.png)




Step 3: enter the copied link with the command line:  

```
sudo wget https://github.com/StartBootstrap/startbootstrap-agency/archive/gh-pages.zip
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/euc515v173qg4usis2ot.png)


Step 4: Unzip the file. Run the command line 
```
sudo unzip gh-pages.zip
```
 you can list (view)

```
ls
```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uo41fxyku3xv3awph4bd.png)


Step 5: now that we have deployed our website, let rename and replace it with our public IP.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/02fjp0eb51zmkr2kkxc5.png)


Now the public IP address is replaced with the website. Let’s confirm on web browser.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ncdiopyoi8du9rgwe7wc.png)




![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/stb7fiu6xpcn0trzs51g.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u50d9e8r1d6tvope2pff.png)



Congratulations! You've successfully deployed a website on a public domain, making it accessible globally. Please note that the website will be available for access within 12 hours after publication. Unfortunately, I won't be able to keep it running indefinitely due to incurred charges.

_URL:_ **34.204.186.40**

Please let me know in the comments if you're able to access the website.

That concludes our Week 4 article! Feel free to reach out to me with questions or to practice what we've covered. Remember, practice is key to mastering these skills.

We're just four weeks away from completing our junior cloud engineering journey! 🚀

Stay awesome, everyone! Looking forward to seeing you in my next article. 😃
