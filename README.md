# aws_project# VPC — Virtual Private Cloud

## What is VPC?
VPC stands for Virtual Private Cloud. It is an isolated network in the cloud where you can launch and manage your resources like EC2, Databases, and Applications securely.

---

## Components of VPC

### 1. Internet Gateway (IGW)
An Internet Gateway helps traffic flow in and out of the VPC. It is connected directly to the VPC and acts like a **main gate** — allowing resources inside the VPC to communicate with the internet.

### 2. Route Tables
A Route Table works like a **direction board** for your network. It tells each subnet where to send traffic — for example, directing a public subnet to connect through the Internet Gateway so traffic can reach the internet.

### 3. Subnets
A Subnet is a **smaller network** created inside a VPC. There are two types:
- **Public Subnet** — Associated with a Public Route Table and the Internet Gateway, allowing direct internet access.
- **Private Subnet** — Associated with a Private Route Table and connected to a NAT Gateway, which then routes traffic through an Elastic IP to reach the internet securely.

### 4. Jump Server / Bastion Host
A Jump Server (also called a Bastion Host) is located inside the **Public Subnet**. It acts as a secure entry point that allows administrators to connect to Private EC2 instances from the internet. It is the only server that has direct internet access for this purpose.

### 5. NAT Gateway
NAT stands for **Network Address Translator**. It is placed inside the Public Subnet and helps Private EC2 instances communicate with the internet by converting their **Private IP address into a Public IP address** — without exposing them directly to the internet.

### 6. Elastic IP Address
An Elastic IP is a **static public IP address** assigned to a server. When a Private EC2 instance wants to communicate with the internet, it first goes through the NAT Gateway, which converts the private IP. The Elastic IP then provides a fixed public address so the traffic can go out to the internet and return back to the correct server.

### 7. Public Subnet
A Public Subnet is a subnet that has **direct access to the internet** through the Internet Gateway. Resources placed here, like a Bastion Host or web servers, can be reached from the internet.

### 8. Private Subnet
A Private Subnet contains resources that have **no direct connection** to the Internet Gateway. It uses a Private Route Table and connects to the internet only through a NAT Gateway — keeping the resources secure and hidden from direct public access.

### 9. Private EC2 Machine
A Private EC2 instance is located inside the Private Subnet. It is used to **host applications, databases, and sensitive data** that should not be directly accessible from the internet. It can only be accessed through the Jump Server / Bastion Host.

---

## VPC Architecture Flow

```
Internet
   |
Internet Gateway (IGW)
   |
Public Subnet
   |-- Bastion Host (Jump Server)
   |-- NAT Gateway ← Elastic IP
         |
      Private Subnet
            |
         Private EC2 (Applications & Data)
```

---

## Key Takeaways
- VPC provides an **isolated and secure** network environment in AWS
- **Public Subnet** = directly accessible from internet via IGW
- **Private Subnet** = no direct internet access, uses NAT Gateway
- **Bastion Host** = secure gateway to access private resources
- **NAT Gateway + Elastic IP** = allows private resources to initiate outbound internet traffic safely

---
*Documented by Madhav S R | AWS Cloud Learner*
