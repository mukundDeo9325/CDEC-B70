## What is a VPC?

A **Virtual Private Cloud (VPC)** is an isolated, logically separated virtual network in AWS where you can launch AWS resources (such as EC2 instances, RDS databases, and load balancers). It gives you full control over your network configuration, including IP addressing, subnets, routing, and security.

## Key Components of a Basic VPC

A minimal, commonly used VPC design contains the following components:

1. **VPC (CIDR Block)**
   - Example CIDR: `10.0.0.0/16`
   - This defines the private IP address range for the entire VPC.

2. **Subnets**
   - **Public Subnet**
     - Example CIDR: `10.0.1.0/24`
     - Has a route to the Internet Gateway, so resources in this subnet can have public internet access (typically via public IPs or Elastic IPs).
   - **Private Subnet** (optional in the most basic design but very common)
     - Example CIDR: `10.0.2.0/24`
     - No direct route to the internet; often used for databases or application servers.

3. **Internet Gateway (IGW)**
   - A horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.
   - Must be **attached to the VPC** and referenced in a **route table** to enable outbound/inbound internet traffic for public subnets.

4. **Route Tables**
   - **Main Route Table**
     - Automatically created with the VPC.
   - **Public Route Table** (commonly a separate custom route table)
     - Has a route like `0.0.0.0/0` → Internet Gateway (IGW).
     - Associated with the public subnet(s).
   - **Private Route Table** (optional for basic, but standard in multi-tier designs)
     - No direct route to IGW; may have routes to a NAT Gateway/Instance for outbound internet, or to a VPN/Transit Gateway for on‑prem connectivity.

5. **Security Groups**
   - Virtual firewalls attached to **ENIs (Elastic Network Interfaces)** or directly to resources like EC2.
   - **Stateful**: If an incoming request is allowed, the response traffic is automatically allowed.
   - Example rules for a web server:
     - Inbound: HTTP (80) and/or HTTPS (443) from `0.0.0.0/0`.
     - Inbound: SSH (22) from your trusted IP only.
     - Outbound: Allow all (`0.0.0.0/0`) by default.

6. **Network ACLs (NACLs)**
   - Optional layer of subnet-level security.
   - **Stateless**: You must specify both inbound and outbound rules.
   - Often left as default (allow all) in simple environments and hardened later.

## Example: Simple Public Web Server VPC

A basic scenario for learning/testing:

- VPC: `10.0.0.0/16`
- One public subnet: `10.0.1.0/24`
- Internet Gateway attached and a route `0.0.0.0/0 → IGW` in the public route table
- Security Group allowing:
  - HTTP (80) from `0.0.0.0/0`
  - SSH (22) from your IP
- EC2 instance in the public subnet with an auto-assigned public IP

This setup allows you to:
- SSH into the instance from your machine
- Access a web server (e.g., Apache, Nginx) running on the instance via the internet

## Basic Steps to Create a VPC (High Level)

1. **Create a VPC** with a CIDR block (e.g., `10.0.0.0/16`).
2. **Create a subnet** (e.g., `10.0.1.0/24`) and mark it as a public subnet.
3. **Create and attach an Internet Gateway** to the VPC.
4. **Create a route table**, add a default route `0.0.0.0/0` pointing to the IGW, and **associate it with the public subnet**.
5. **Create a security group** with appropriate inbound/outbound rules.
6. **Launch an EC2 instance** in the public subnet, associate the security group, and enable auto-assign public IP.

## Best Practices (For Basic Designs)

- Use **multiple Availability Zones** (AZs) for high availability (e.g., one subnet per AZ).
- Separate **public** and **private** subnets:
  - Public: Load balancers, bastion hosts, NAT gateways.
  - Private: Application servers, databases, internal services.
- Restrict management access (SSH/RDP) to known IP addresses or via a bastion host/VPN.
- Use **tags** (Name, Environment, Owner, Project) to keep resources organized.

