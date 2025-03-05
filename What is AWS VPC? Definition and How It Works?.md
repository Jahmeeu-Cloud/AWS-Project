## Project: Creating Amazon Web Service (AWS) Virtual Private Cloud (VPC)

What is AWS VPC? Definition?

A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.


How It Works?

A VPC provides a customizable, software-defined network (SDN) within the cloud, enabling:

Key Features:

1. Resource Management: Provision and manage EC2 instances, RDS databases, and S3 storage.
2. Network Segmentation: Define CIDR blocks, create subnets, and organize resources.
3. Traffic Control: Configure gateways, route tables, and network ACLs for secure traffic flow.
4. Access Control: Establish security groups, NACLs, and firewall rules for protected resource access.

Benefits:

- Logical isolation from other networks
- Enhanced data and application security
- Customizable network configurations
- Regulated inter-resource communication

VPC Implementation:

Follow along as we deploy this project in steps:

Section A: Create VPC 
Section B: Provision resources (EC2)
Section C: Create Python application and run the project.

Get ready to secure your cloud infrastructure with VPC!



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jub63nx9cl8659yvj80z.png)



This example showcases creating a resilient VPC for production servers:

First login to your AWS console.

Section A: Setting up VPC on AWS console.

Step 1: Locate the search bar and type “VPC”


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h7cxh44geyb9zyvlpvfn.png)

Step 2: This is how VPC will look like in Dashboard and click on VPC.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/r7en5zvvf0783ueqdf2y.png)


Step 3: name your project to VPC 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bc54atuyq9w9i4i014iz.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6a5n8amkro05xmdjsn94.png)



Step 4: set it as default


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hgtbtyn56zmxf3zs93t3.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cwofj6lvsbm5j0l42wib.png)


Step 5: click on create VPC, this is how successful VPC is created.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lq0zhqp74wcoippi882g.png)


Step 6: Click on view VPC, and go to resource map.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gjjst4eyxdlcajjabk9i.png)



Section B: create an EC2 Instance.  Login and connect with your terminal.

Step 1: Search for EC2


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3r3o405r8hmqlmjyy7pm.png)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rcw0fk2jx134eg0bhvka.png)

Step 2: Selecting the right region and name your EC2 instance, select preferred Linux distribution (Ubuntu)



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/of6u9ysi05dp82jf3rru.png)


Step 3: select free tier option for AMI (preferred) and select your pem key or create one.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/01pfogdly534eg2huynt.png)


Step 4: click on **edit** in network settings and select the option in the diagram, make sure you select the demo-VPC created and you can rename your security group name for easy identification.



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6gxdgn8ujwhysu5wedi5.png)


Step 5: Leave the rest as default and click on launch instances.


Section C: Install the python application and the test run the security / vpc we created using terminal.


Step 1: Go to your new instance created, Click on connect.



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cnoklqxx8xotinbqhuy1.png)


Step 2: Open your terminal (Git Bash) and connect your EC2 instance.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/djzpfrceh6cl11qrttx0.png)
> Comments:
>  Make sure you change your directory where your pem key then connect using this cmd line:
> ssh –i  key.pem  username@host 
> ssh –i cloud-jay-key.pem Ubuntu@34.236.38.205


step 3: update the packages this cmd line: 

```
sudo apt update
```

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3vf7l2e5uar1h85iuu8z.png)

Step 4: check if python is installed with cmd line:
“Python3 –version”


Step 5: run the application the cmd line:
python3 –m http.server 8000


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c4q3yy53hddl8pomfd3e.png)

Step 6: Run the python application on web run it with the ip
http:// 54.236.38.205:8000 


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yxnfwz26d90l3h55kbuk.png)
You can see it is not accessible


Step 7: Go to vpc and check for Network NACL under security.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c6s91jl60qhd96dp3kp7.png)



Step 8: You can see it is set and okay, let’s go security group.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9id8lwewwbnvlwd5381h.png)


Step 9: Go to Security groups, make sure you select the right security group id for demo-vpc, open it and check if the right port is open, which Custom TCP port 8000


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bvbjindg2d3kk8znqupx.png)


Step 10: Edit the inbound rules.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xxfpk7oovka6uktasnyy.png)


Step 11: Under Inbound rules, add a new rule name custom TCP, add port 8000, under source select ip version 4 and save it and open the Python app again.
 
 
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1gb03u338gt6m5sn74kv.png)


Step 12: Congratulation, Python app is accessible now.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c2br1ykoe2cg264swmpt.png)


Glossary

VPC: A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.


Subnet: A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.


IP addressing: You can assign IP addresses, both IPv4 and IPv6, to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as EC2 instances, NAT gateways, and Network Load Balancers.


Network Access Control List (NACL): A Network Access Control List is a stateless firewall that controls inbound and outbound traffic at the subnet level. It operates at the IP address level and can allow or deny traffic based on rules that you define. NACLs provide an additional layer of network security for your VPC.



Security Group (SG): A security group acts as a virtual firewall for instances (EC2 instances or other resources) within a VPC. It controls inbound and outbound traffic at the instance level. Security groups allow you to define rules that permit or restrict traffic based on protocols, ports, and IP addresses.  



Route table: Use route tables to determine where network traffic from your subnet or gateway is directed.



Gateway: A gateway connects your VPC to another network. For example, use an internet gateway to connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately, without the use of an internet gateway or NAT device.
Peering connections: Use a VPC peering connection to route traffic between the resources in two VPCs.
Traffic Mirroring: Copy network traffic from network interfaces and send it to security and monitoring appliances for deep packet inspection.


Transit gateways: Use a transit gateway, which acts as a central hub, to route traffic between your VPCs, VPN connections, and AWS Direct Connect connections.
VPC Flow Logs: A flow log captures information about the IP traffic going to and from network interfaces in your VPC.
VPN connections: Connect your VPCs to your on-premises networks using AWS Virtual Private Network (AWS VPN).


Resources:
VPC with servers in private subnets and NAT
https://docs.aws.amazon.com/vpc/latest/userguide/vpc-example-private-subnets-nat.html
