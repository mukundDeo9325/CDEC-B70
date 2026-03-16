# Launch EC2 Instance in Public Subnet

The goal of this lab is to launch a single EC2 instance in a public subnet that is accessible from the Internet via SSH.

---

## Architecture Diagram

<img src="./images/ec2_instance.png" alt="EC2 instance architecture" width="750">

---

## Overview

To achieve the goal of this lab, follow the steps below.

### 1. Launch EC2 Instance
![launch_instance](./images/Click_lanch_ec2.png)

---

### 2. Choose AMI (Operating System)

Select the required **Amazon Machine Image (AMI)**.

More info:  
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html

![choose_ami](./images/Select_ami.png)

---

### 3. Select Instance Type

Choose the required **Instance Type**.

More info:  
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html

![instance_type](./images/Instance_type_selecation.png)

---

### 4. Configure Network Settings

Ensure **Auto Assign Public IP** is **Enabled**.

![network_selection](./images/Network_public_subnet.png)

---

### 5. Configure Storage

Review and configure storage settings as needed.

---

### 6. Add Tags (Optional)

Tags help identify resources.

Example:
Key: Name
Value: Test-Server


---

### 7. Configure Security Group

Add inbound rules to allow required traffic.

Example:
- SSH (22) → Your IP
- HTTP (80) → Anywhere

More info:  
https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html

![security_group](./images/SG_inbount_port.png)

---

### 8. Create / Select Key Pair

Select an existing **EC2 key pair** or create a new one.

More info:  
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html

![key_pair](./images/Key_pair_select.png)

---

### 9. Advanced Options – Run User Data Script

#### Apache Server Setup

```bash
#!/bin/bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
echo "This is test server $HOSTNAME" > /var/www/html/index.html
```




