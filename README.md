# AWS VPC Setup – Public and Private Subnets
AWS VPC Architecture Setup (Public &amp; Private Subnets)

## 🎯 Overview
This project demonstrates a custom VPC setup in AWS with public and private subnets, a bastion host, and a private EC2 instance accessible only through the bastion host. The private instance was also configured for outbound internet access using a NAT Gateway.

---

## 🏗️ Implementation Steps

- **VPC**
  - Created a custom VPC with a defined IPv4 CIDR block.

- **Internet Gateway (IGW)**
  - Created an Internet Gateway and attached it to the VPC.

- **Subnets**
  - Created public subnets with auto-assign public IPs enabled.
  - Created private subnets with no public IPs.
  - Distributed subnets across different Availability Zones.

- **NAT Gateway**
  - Deployed a NAT Gateway in a public subnet.
  - Allocated and attached an Elastic IP for outbound access.

- **Route Tables**
  - Configured a Public Route Table with a route to the IGW.
  - Configured a Private Route Table with a route to the NAT Gateway.

- **Subnet Associations**
  - Associated the public subnets with the Public Route Table.
  - Associated the private subnets with the Private Route Table.

- **Security Groups**
  - Created a Bastion Host Security Group allowing SSH access from my local IP.
  - Created a Private Instance Security Group allowing SSH access only from the Bastion Host SG.

- **EC2 Instances**
  - Launched a public EC2 instance (Bastion Host) in the public subnet with a public IP.
  - Launched a private EC2 instance in the private subnet without a public IP.

- **Connectivity Tests**
  - Successfully connected to the Bastion Host via SSH from my local machine.
  - From the Bastion Host, connected to the private EC2 instance using its private IP.
  - Verified that the private EC2 had no internet access initially.
  - After attaching the NAT Gateway, confirmed outbound internet access from the private instance (tested using ping and package updates).

---
