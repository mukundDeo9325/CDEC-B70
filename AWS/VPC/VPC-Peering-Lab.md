# Lab: Create a VPC Peering Connection (Same Account, Same Region)

This lab walks you through creating a **VPC peering connection** between two VPCs in the **same AWS account and same region**, and then testing connectivity between EC2 instances in each VPC.

> Estimated time: 45–60 minutes

---

## 1. Lab Architecture

You will create:

- **VPC A (Requester VPC)**
  - CIDR: `10.0.0.0/16`
  - One public subnet: `10.0.1.0/24`
  - 1 EC2 instance in the public subnet

- **VPC B (Accepter VPC)**
  - CIDR: `10.1.0.0/16`
  - One public subnet: `10.1.1.0/24`
  - 1 EC2 instance in the public subnet

Then you will:

- Create a **VPC peering connection** between VPC A and VPC B
- Update **route tables** and **security groups**
- Test connectivity (ping/SSH) between the instances using their **private IPs**

> Note: Make sure the CIDR blocks **do not overlap**.

---

## 2. Prerequisites

- An AWS account with permissions to create VPCs, subnets, EC2 instances, and VPC peering connections
- A key pair available in the chosen region (or create a new one)
- Basic familiarity with the AWS Management Console

> In this lab we assume everything is created in a **single region** (e.g., `ap-south-1` or `us-east-1`).

---

## 3. Create VPC A (Requester)

1. In the AWS Console, go to **VPC** service.
2. In the left menu, click **Your VPCs** → **Create VPC**.
3. Choose **VPC only**.
4. Configure:
   - Name tag: `VPC-A`
   - IPv4 CIDR: `10.0.0.0/16`
   - Tenancy: `Default`
5. Click **Create VPC**.

### 3.1 Create a Public Subnet in VPC A

1. Go to **Subnets** → **Create subnet**.
2. VPC ID: select **VPC-A**.
3. Subnet name: `VPC-A-Public-Subnet`
4. Availability Zone: choose any AZ (e.g., `ap-south-1a`).
5. IPv4 CIDR block: `10.0.1.0/24`
6. Click **Create subnet**.

### 3.2 Enable Auto-Assign Public IP for the Subnet (Optional but Helpful)

1. Select `VPC-A-Public-Subnet`.
2. Click **Actions** → **Edit subnet settings** (or **Edit subnet attributes**).
3. Enable **Auto-assign IP settings** → check **Enable auto-assign public IPv4 address**.
4. Save changes.

### 3.3 Create and Configure Internet Gateway for VPC A (Optional, for internet access)

1. Go to **Internet gateways** → **Create internet gateway**.
2. Name tag: `VPC-A-IGW` → **Create internet gateway**.
3. Select `VPC-A-IGW` → **Actions** → **Attach to VPC** → choose **VPC-A** → **Attach**.

4. Go to **Route tables**.
5. Find the route table associated with `VPC-A-Public-Subnet` (or create a new one and associate it).
6. Edit routes:
   - Add route: `0.0.0.0/0` → target: **Internet Gateway (VPC-A-IGW)**.
7. Save changes.

---

## 4. Create VPC B (Accepter)

1. Go to **Your VPCs** → **Create VPC**.
2. Choose **VPC only**.
3. Configure:
   - Name tag: `VPC-B`
   - IPv4 CIDR: `10.1.0.0/16`
4. Click **Create VPC**.

### 4.1 Create a Public Subnet in VPC B

1. Go to **Subnets** → **Create subnet**.
2. VPC ID: select **VPC-B**.
3. Subnet name: `VPC-B-Public-Subnet`
4. Availability Zone: you may use the same AZ as VPC A for simplicity.
5. IPv4 CIDR block: `10.1.1.0/24`
6. Click **Create subnet**.

### 4.2 (Optional) Internet Gateway for VPC B

If you also want VPC B to have internet access:

1. Create an IGW named `VPC-B-IGW`.
2. Attach it to **VPC-B**.
3. Update the associated route table with `0.0.0.0/0` → `VPC-B-IGW`.

---

## 5. Launch EC2 Instances in Each VPC

You will launch very small instances (e.g., `t2.micro` or `t3.micro`) in each public subnet.

### 5.1 EC2 in VPC A

1. Go to **EC2** → **Instances** → **Launch instances**.
2. Name: `Instance-A`.
3. AMI: choose a small Linux AMI (e.g., Amazon Linux 2).
4. Instance type: `t2.micro` (or free tier eligible).
5. Key pair: select/create one.
6. Network settings:
   - VPC: **VPC-A**
   - Subnet: `VPC-A-Public-Subnet`
   - Auto-assign public IP: **Enable**
7. Security group: create a new SG `SG-VPC-A` with rules:
   - Inbound: **SSH (22)** from your IP
   - Inbound: **ICMP (Echo Request)** from `10.1.0.0/16` (to allow ping from VPC B)
   - Outbound: allow all (default)
8. Launch the instance.

### 5.2 EC2 in VPC B

1. Launch another instance named `Instance-B`.
2. Same AMI and instance type.
3. Network settings:
   - VPC: **VPC-B**
   - Subnet: `VPC-B-Public-Subnet`
   - Auto-assign public IP: Enable (for SSH from your machine)
4. Security group: create `SG-VPC-B` with rules:
   - Inbound: **SSH (22)** from your IP
   - Inbound: **ICMP (Echo Request)** from `10.0.0.0/16`
   - Outbound: allow all (default)
5. Launch the instance.

Wait until both instances are in **running** state.

---

## 6. Create the VPC Peering Connection

1. Go to **VPC** → **Peering connections** → **Create peering connection**.
2. Settings:
   - Name tag: `VPC-A-to-VPC-B`
   - VPC (Requester): select **VPC-A (10.0.0.0/16)**
   - VPC (Accepter): select **VPC-B (10.1.0.0/16)** (same account, same region)
3. Click **Create peering connection**.
4. After creation, select the new peering connection.
5. Click **Actions** → **Accept request**.
6. Status should change to **Active**.

At this point, the VPCs are peered, but traffic will not flow until you update **route tables**.

---

## 7. Update Route Tables for Peering

### 7.1 Route Table for VPC A

1. In the VPC console, go to **Route tables**.
2. Find the route table associated with `VPC-A-Public-Subnet`.
3. Select it and go to the **Routes** tab → **Edit routes** → **Add route**.
4. Add route:
   - Destination: `10.1.0.0/16` (CIDR of VPC B)
   - Target: **Peering connection** → select `VPC-A-to-VPC-B`
5. Save changes.

### 7.2 Route Table for VPC B

1. Find the route table associated with `VPC-B-Public-Subnet`.
2. Edit routes and add:
   - Destination: `10.0.0.0/16` (CIDR of VPC A)
   - Target: **Peering connection** → `VPC-A-to-VPC-B`
3. Save changes.

Now traffic between the two CIDR ranges will be forwarded through the peering connection.

---

## 8. Test Connectivity Between Instances

### 8.1 Get Private IPs

1. Go to **EC2 → Instances**.
2. Note the **private IPv4** address of `Instance-A` (in VPC A).
3. Note the **private IPv4** address of `Instance-B` (in VPC B).

### 8.2 SSH Into One Instance and Ping the Other

1. From your local machine, SSH into `Instance-A` using its **public IP**:

   ```bash path=null start=null
   ssh -i /path/to/your-key.pem ec2-user@<Instance-A-Public-IP>
   ```

2. Once logged into `Instance-A`, ping `Instance-B` using its **private IP**:

   ```bash path=null start=null
   ping <Instance-B-Private-IP>
   ```

3. You should see successful ICMP replies.

4. Optionally, SSH from `Instance-A` to `Instance-B` (if allowed by SGs) using the private IP.

If the ping fails, check:

- Route tables (do they have routes pointing to the peering connection?)
- Security groups (do they allow ICMP from the other VPC CIDR?)
- NACLs (are they allowing traffic between those CIDR ranges?)

---

## 9. Clean Up Resources

To avoid unnecessary charges, delete resources created for this lab:

1. **Terminate EC2 instances** `Instance-A` and `Instance-B`.
2. **Delete the VPC peering connection** (`VPC-A-to-VPC-B`).
3. **Delete subnets** in VPC A and VPC B.
4. **Detach and delete Internet Gateways** for both VPCs.
5. **Delete VPC-A** and **VPC-B**.

---

