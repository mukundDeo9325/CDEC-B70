The goal of this lab is to launch a single EC2 instance in a public subnet that is accessible from the Internet via SSH.

## Architecture Diagram
<img src="../images/ec2_instance.png" alt="EC2 instance" width="750">



## Overview

 In order to achieve the goal of this lab, you will have to go through the following steps:
![lanch_instance](./images/Click_lanch_ec2.png)

1. Choose the operating system by selecting the [Amazon Machine Image (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html).
![chose_ami](./images/Select_ami.png)
2. Define the virtual hardware configuration by choosing an [Instance Type](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html).
![instance_type](./images/Instance_type_selecation.png)

3. Review the network settings.
check weather auto assing public ip is on or not --> enable
![network_selection](./images/Network_public_subnet.png)

4. Review the storage settings.
5. Create tags (optional).

6. Configure the [Security Group](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html) rules (firewall).
![sequrity_group](./images/SG_inbount_port.png)

7. Launch the instance (choosing or creating an [EC2 key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)).
![key_pair](./images/Key_pair_select.png)

8. advance option run simple bash script
   ![bash_script](./images/Bash_script.png)
 ```bash
  #!/bin/bash 
sudo -i 
apt install apache2 -y 
systemctl start apache2 
systemctl enable apache2 
echo "this is test server $HOSTNAME" >/var/www/html/index.html
```
9. server check
   ![serevr_check](./images/check_server_HTTP.png)
10. if want to connect to instance click on connect
    ![connect](./images/ssh_public_ec2.png)
    
