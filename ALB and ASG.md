## **1. Introduction**
This document provides a comprehensive guide on setting up and managing an **Application Load Balancer (ALB)** and **Auto Scaling Group (ASG)** in AWS. These services enhance application availability, distribute traffic efficiently, and ensure scalability based on demand.

## **2. Application Load Balancer (ALB)**
### **2.1 Overview**
An Application Load Balancer (ALB) is a Layer 7 (HTTP/HTTPS) load balancer that distributes incoming traffic across multiple targets such as Amazon EC2 instances, containers, and IP addresses. ALB supports advanced request routing and is optimized for microservices and containerized applications.

### **2.2 Key Features**
- **Path-Based Routing**: Routes requests based on the URL path.
- **Host-Based Routing**: Routes traffic based on the requested hostname.
- **SSL Termination**: Offloads SSL decryption to improve backend performance.
- **Sticky Sessions**: Ensures user requests go to the same backend instance.
- **Health Checks**: Monitors target health and routes traffic only to healthy instances.

### **2.3 Steps to Create an ALB**
1. **Navigate to the AWS Console** → EC2 → Load Balancers → **Create Load Balancer**.
2. **Select Application Load Balancer**.
3. **Configure the ALB**:
   - Name: `my-alb`
   - Scheme: **Internet-facing** (or Internal for private applications)
   - IP Type: IPv4
   - Listeners: **HTTP (80)** or **HTTPS (443)**
4. **Assign Public Subnets** to the ALB.
5. **Create a Security Group**:
   - Allow HTTP/HTTPS from **0.0.0.0/0**.
6. **Create a Target Group**:
   - Choose **Instances** as the target type.
   - Protocol: **HTTP**
   - Port: **80**
   - Attach registered EC2 instances.
7. **Review and Create the ALB**.

### **2.4 Testing the ALB**
- Copy the **ALB DNS name** and access it in a browser.
- The request should be forwarded to one of the registered instances.

---

## **3. Auto Scaling Group (ASG)**
### **3.1 Overview**
An Auto Scaling Group (ASG) ensures that the correct number of EC2 instances are running based on demand. It automatically scales up instances during high traffic and scales down when demand decreases.

### **3.2 Key Features**
- **Automatic Scaling**: Adjusts instance count dynamically.
- **Health Checks & Auto Healing**: Replaces unhealthy instances.
- **Integration with ALB**: Distributes traffic evenly across instances.
- **Scheduled Scaling**: Increases or decreases capacity at specific times.

### **3.3 Steps to Create an ASG**
1. **Navigate to the AWS Console** → EC2 → **Auto Scaling Groups** → **Create ASG**.
2. **Select a Launch Template** or **Launch Configuration**.
3. **Configure the ASG**:
   - Min Desired Capacity: `2`
   - Desired Capacity: `2`
   - Max Desired Capacity: `4`
4. **Attach the Target Group** created for the ALB.
5. **Define Scaling Policies**:
   - Scale based on **CPU Utilization**.
   - Example: Increase instances when CPU exceeds **70%**.
6. **Set up Notifications** (optional):
   - Configure Amazon SNS to receive alerts on scaling events.
7. **Review and Create the ASG**.

### **3.4 Testing the ASG**
- Copy the **ALB DNS name** and check if traffic is distributed.
- Manually **terminate an EC2 instance** → ASG should replace it automatically.
- Simulate high CPU usage → ASG should scale out (add instances).

---

## **4. Monitoring & Optimization**
### **4.1 Monitoring with CloudWatch**
- **Go to AWS CloudWatch → Metrics → EC2 → Auto Scaling**.
- Track key metrics like:
  - **CPU Utilization**
  - **Request Count per Target** (ALB)
  - **HealthyHostCount**
  
### **4.2 Cost Optimization**
- Use **Spot Instances** for cost savings.
- Set **lower scaling limits** to avoid excessive scaling.
- Enable **termination protection** for critical instances.

---

## **5. Conclusion**
By implementing **Application Load Balancer (ALB) and Auto Scaling Group (ASG)**, organizations can achieve **high availability, fault tolerance, and cost-efficient scaling** for their applications. AWS provides automation tools like **CloudWatch** to monitor performance and optimize scaling strategies efficiently.

---
Screenshot of the projects:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zhxh6bjw1nor31s0uow7.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dwifrf5fn0g2mdhsu84f.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yshb2vv3dlk7cbcnmt20.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ubbyzhjuz4sl6s5fvhq1.png)

---

This is my Cloudwatch, where am monitoring it.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/whe8d3wvg70mngqvfvp3.png)

---

Auto Scaling Group ASG has automatically increased my Instance

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sntrvvz83r7dby2taf0k.png)



For further details, refer to [AWS Documentation](https://docs.aws.amazon.com/).

