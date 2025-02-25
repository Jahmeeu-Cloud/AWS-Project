# Installing-and-configuring-the-Amazon-CloudWatch-Agent-on-Amazon-Linux-and-Ubuntu

## **🚀 Deploying Amazon CloudWatch Agent on Amazon Linux & Ubuntu**  


Today, I successfully installed and configured the **Amazon CloudWatch Agent** on both **Amazon Linux** and **Ubuntu**! 🎯  

This task involved setting up system metrics and log monitoring for EC2 instances, ensuring that CPU, memory, disk usage, and application logs are seamlessly sent to **Amazon CloudWatch** for analysis.  

Below is a step-by-step outline to achieve this on both **Amazon Linux** and **Ubuntu**.  

---

### **📌 Amazon Linux: Installing & Configuring CloudWatch Agent**
1️⃣ **Update the system**  
   ```bash
   sudo yum update -y
   ```

2️⃣ **Install CloudWatch Agent**  
   ```bash
   sudo yum install -y amazon-cloudwatch-agent
   ```

3️⃣ **Run the Configuration Wizard**  
   ```bash
   sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
   ```

4️⃣ **Start the CloudWatch Agent**  
   ```bash
   sudo systemctl enable amazon-cloudwatch-agent
   sudo systemctl start amazon-cloudwatch-agent
   ```

5️⃣ **Verify the status**  
   ```bash
   sudo systemctl status amazon-cloudwatch-agent
   ```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sx42bshibn0aampedm6p.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6a8m5ncl33eywsrp6y4a.png)





---

### **📌 Ubuntu: Installing & Configuring CloudWatch Agent**
1️⃣ **Update the system**  
   ```bash
   sudo apt update -y
   ```

2️⃣ **Download CloudWatch Agent**  
   ```bash
   curl -O https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb
   ```

3️⃣ **Install the Agent**  
   ```bash
   sudo dpkg -i amazon-cloudwatch-agent.deb
   ```

4️⃣ **Run the Configuration Wizard**  
   ```bash
   sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
   ```

5️⃣ **Enable and Start CloudWatch Agent**  
   ```bash
   sudo systemctl enable amazon-cloudwatch-agent
   sudo systemctl start amazon-cloudwatch-agent
   ```

6️⃣ **Check the Agent Status**  
   ```bash
   sudo systemctl status amazon-cloudwatch-agent
   ```


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cf72oyua14jgfnl1g9bn.png)






---

### **🔍 Key Takeaways**
✅ Amazon CloudWatch Agent helps monitor EC2 instances and applications in real-time.  
✅ **Amazon Linux** supports direct installation via **yum**, while **Ubuntu** requires manual package installation.  
✅ Logs and metrics can be customized via `/opt/aws/amazon-cloudwatch-agent/bin/config.json`.  
✅ Using **AWS Systems Manager Parameter Store**, configurations can be centrally managed across multiple instances.  

---

### **🚀 Next Steps**
I’ll be diving deeper into **CloudWatch Logs Insights** to analyze application performance and troubleshoot issues effectively!  

If you're working on **AWS observability**, let’s connect and share insights! What’s your experience with CloudWatch Agent? Drop your thoughts in the comments! ⬇️  

#AWS #CloudEngineering #AmazonLinux #Ubuntu #DevOps #CloudWatch #Monitoring
