
# Introduction to VPC

## What is a VPC?
Amazon Virtual Private Cloud (VPC) allows you to launch AWS resources in a logically isolated network that you define. You have complete control over your virtual networking environment, including selecting your own IP address range, creating subnets, and configuring route tables and gateways.

### Key Features of a VPC:
- **Logical Isolation:** Operates within a region, providing control over network setup.
- **Subnets:** Divide your VPC into smaller segments based on your requirements.
- **Security:** Use security groups and network ACLs for fine-grained control.
- **Internet Gateway:** Attach to a VPC for internet access.
- **Private Connectivity:** Use VPN or Direct Connect to connect on-premises environments.
- **Elastic IPs:** Assign static IP addresses to resources in your VPC.

### VPC Types:
1. **Default VPC:** Automatically created by AWS in each region. It includes a public subnet in each Availability Zone, enabling immediate access to AWS services.
2. **Custom VPC:** Created manually to meet specific networking requirements, offering full control over the network configuration.

### Reserved IPs in AWS:
Within each subnet's CIDR block, AWS reserves the following IP addresses:
- **.0:** Network address.
- **.1:** Reserved by AWS for the VPC router.
- **.2:** Reserved for mapping Amazon-provided DNS.
- **.3:** Reserved for future use.
- **Last IP:** Reserved for the network broadcast address. 

For example, in a `/24` subnet (`192.168.1.0/24`):
- Reserved IPs: `192.168.1.0`, `192.168.1.1`, `192.168.1.2`, `192.168.1.3`, and `192.168.1.255`.

---

# CIDR Calculation for Subnets

## What is CIDR?
Classless Inter-Domain Routing (CIDR) is a method for allocating IP addresses and routing. Instead of using the traditional class-based system, CIDR allows IP ranges to be split into subnets with flexible sizes.

### CIDR Notation:
A CIDR block is expressed as `IP address/prefix length`. For example, `192.168.0.0/24`:
- **192.168.0.0**: Network portion.
- **/24**: Indicates that the first 24 bits represent the network, leaving 8 bits for host addresses.

### Subnetting Calculation:
1. **Determine the Number of Hosts:**
   - Formula: `2^(32 - prefix length) - 2`
   - Example: `/24` = `2^(32 - 24) - 2 = 254 usable hosts`

2. **Divide a Larger Block:**
   - Example: To split `10.0.0.0/16` into four subnets, increase the prefix length to `/18`. Resulting subnets:
     - `10.0.0.0/18`
     - `10.0.64.0/18`
     - `10.0.128.0/18`
     - `10.0.192.0/18`

### Practical Example:
- **Base CIDR:** `10.0.0.0/16`
- **Required Subnets:** 4
- **Step:** Adjust prefix length to `/18` to accommodate each subnet.

---


# Create VPC and Subnet

## Step-by-Step Guide:

### Create a VPC:
1. Log in to the **AWS Management Console**.
2. Navigate to **VPC Dashboard**.
3. Click **Create VPC**.
4. Provide details:
   - **Name:** MyVPC
   - **IPv4 CIDR Block:** `10.0.0.0/16`
   - Enable DNS settings if required.
5. Click **Create VPC**.

### Create a Subnet:
1. Go to the **Subnets** section in the VPC Dashboard.
2. Click **Create Subnet**.
3. Select your VPC (e.g., `MyVPC`).
4. Specify details:
   - **Name:** PublicSubnet
   - **Availability Zone:** Choose an AZ (e.g., us-east-1a).
   - **CIDR Block:** `10.0.0.0/24`
5. Click **Create Subnet**.

### Verify:
1. Go to the **VPC Dashboard**.
2. Confirm that your VPC and Subnet appear in the list.
3. Associate your subnet with a route table if necessary.

---
