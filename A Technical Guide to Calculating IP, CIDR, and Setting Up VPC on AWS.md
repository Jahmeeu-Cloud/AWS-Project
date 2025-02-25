### **Understanding Key Networking Concepts**

Before diving into subnet calculations and setting up a VPC on AWS, it’s crucial to understand the foundational concepts.

#### **1. What is an IP Address?**
An IP (Internet Protocol) address is a unique numerical label assigned to devices connected to a network. It identifies both the network and the device on that network. For example, `192.168.1.1` is a private IP address often used in home networks.

IP addresses come in two versions:
- **IPv4**: A 32-bit address system, e.g., `192.168.1.1`. It supports approximately 4.3 billion addresses.
- **IPv6**: A 128-bit address system, e.g., `2001:0db8:85a3::8a2e:0370:7334`. It provides a much larger address space.

#### **2. What is a VPC?**
A **VPC (Virtual Private Cloud)** is a logically isolated network within a cloud environment. In AWS, a VPC allows you to launch resources such as EC2 instances in a secure network. You define your VPC’s IP range using a CIDR block.

After Creating VPC

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0o7hluwcang2yvrr30go.png)



#### **3. What is CIDR?**
CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and efficiently managing IP networks. CIDR blocks are written in the format `IP/Prefix`, where the prefix determines the network size.

For example:
- **`192.168.1.0/24`**: The `/24` means the first 24 bits are reserved for the network, leaving 8 bits for hosts. This gives 256 total IPs (254 usable, excluding network and broadcast addresses).

| Prefix | Total IPs | Usable IPs |
|--------|-----------|------------|
| /16    | 65,536    | 65,534     |
| /24    | 256       | 254        |
| /25    | 128       | 126        |
| /26    | 64        | 62         |
| /27    | 32        | 30         |

Check end of page to see sample of my calculation I did.

#### **4. What is Subnetting?**
Subnetting divides a larger network into smaller, isolated networks (subnets). Each subnet has its own range of IP addresses, allowing better organization and security.

For example, a VPC with a CIDR block of `172.16.0.0/24` can be divided into smaller subnets:
- Subnet 1: `172.16.0.0/25` (128 IPs)
- Subnet 2: `172.16.0.128/26` (64 IPs)
- Subnet 3: `172.16.0.192/27` (32 IPs)

#### **5. Reserved IP Addresses**
AWS reserves 5 IP addresses in every subnet:
1. **Network Address**: The first IP in the range.
2. **Gateway Address**: The second IP, used as the default gateway.
3. **DNS Reserved**: The third IP, for AWS DNS.
4. **Future Use**: The fourth IP.
5. **Broadcast Address**: The last IP in the range.

---

### **Calculating Subnet Ranges**

#### **Step-by-Step Subnet Calculation**
Let’s say you have a VPC with a CIDR block of `172.16.0.0/24`, and you need the following subnets:
1. Subnet 1: 80 IPs
2. Subnet 2: 50 IPs
3. Subnet 3: 20 IPs

#### **Step 1: Determine Subnet Sizes**
Each subnet must be sized to the nearest power of 2 that accommodates the required IPs:
- Subnet 1: Requires 80 IPs → Nearest power of 2 = 128 IPs → CIDR = `/25`.
- Subnet 2: Requires 50 IPs → Nearest power of 2 = 64 IPs → CIDR = `/26`.
- Subnet 3: Requires 20 IPs → Nearest power of 2 = 32 IPs → CIDR = `/27`.




#### **Step 2: Allocate Non-Overlapping Ranges**
Start each subnet at the next available boundary:
1. Subnet 1: `172.16.0.0/25` → IP Range: `172.16.0.0 - 172.16.0.127`
2. Subnet 2: `172.16.0.128/26` → IP Range: `172.16.0.128 - 172.16.0.191`
3. Subnet 3: `172.16.0.192/27` → IP Range: `172.16.0.192 - 172.16.0.223`


---
Subnet 1


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tky4m4ynqn30rbqdstyz.png)


---
Subnet 2


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6z1gfdy46c9hl5e5cexj.png)


---
Subnet 3

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4xqbi0qs90rsonurb7ph.png)

---

### **Setting Up a VPC on AWS**

#### **Step 1: Create a VPC**
1. Log in to the AWS Management Console.
2. Go to **VPC** > **Create VPC**.
3. Enter the following details:
   - **Name**: `MyVPC`
   - **IPv4 CIDR block**: `172.16.0.0/24`
4. Click **Create VPC**.

---
#### **Step 2: Create Subnets**
1. Navigate to **Subnets** > **Create Subnet**.
2. For Subnet 1:
   - **Name**: `Subnet1`
   - **VPC**: Select `MyVPC`.
   - **CIDR Block**: `172.16.0.0/25`
3. Repeat for Subnet 2 (`172.16.0.128/26`) and Subnet 3 (`172.16.0.192/27`).


This is the outcome after successfully creating the VPC, CIDR, and Subnet.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i2nr1d7vg2yrmwisyri5.png)

---


#### **Step 3: Create an Internet Gateway**
1. Go to **Internet Gateways** > **Create Internet Gateway**.
2. Attach the Internet Gateway to `MyVPC`.

---

#### **Step 4: Update Route Tables**
1. Go to **Route Tables** and find the route table associated with `MyVPC`.
2. Add a route:
   - **Destination**: `0.0.0.0/0`
   - **Target**: Select the Internet Gateway.
3. Associate the route table with your subnets.

---
 
#### **Step 5: Launch an EC2 Instance**
1. Navigate to **EC2** > **Launch Instance**.
2. Select an Amazon Machine Image (AMI).
3. Choose an instance type (e.g., t2.micro).
4. Place the instance in one of your subnets (e.g., `Subnet1`).
5. Assign a public IP to enable internet access.

---



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x3s4npa0vu2wncy4lp38.png)



Here is my calculation, and you can use it as a reference or formula.


---

### **Conclusion**
Subnetting and setting up a VPC may seem intimidating at first, but with a solid understanding of CIDR and IP address allocation, it becomes straightforward. Following the steps above ensures your AWS network is organized, secure, and scalable.

Feel free to share your thoughts or ask questions in the comments below!

