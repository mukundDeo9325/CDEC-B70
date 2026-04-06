## What is Bastion Host?
A Bastion host is a special-purpose server or an instance that is used to configure to work against attacks or threats. It is also known as the 'jump box' that acts like a proxy server and allows the client machines to connect to the remote server. It is basically a gateway between the private subnet and the internet. It allows the user to connect a private network from an external network and act as a proxy to other instances. (refrance: https://www.geeksforgeeks.org/blogs/what-is-aws-bastion-host/)

## Architecture Diagram
![Architecture diagram](../images/jump_server.gif)

# Step 1 - Create VPC
Create a new VPC with the Name tag "jump_server" and the IPv4 CIDR block 192.168.0.0/16.
![step 1](../images/vpc.png)
.
![step 1](../images/vpc2.png)
.
![step 1](../images/vpc3.png)

# step 2 - create subnet (public and private subnet 
## create public subnet using vpc "jump_server"--> ipv4 CIDR block 192.168.10.0/21 public subnet 
![step 2](../images/create_subnet.png)
.
![step 2](../images/chose_vpc.png)
.
![step 2](../images/Public_subnet.png)

## create private subnet IPv4 CIDR block 192.168.0.0/21 private subnet 
![step 2](../images/private_subnet.png)

## show all the created subnets 
![step 2](../images/Subnet_created.png)

# step 3 - create Internet Getway 
![step 3](../images/Create_name2.png)

## navigate to action --> attach to vpc 
select the vpc to attach internet getway 
![step 3](../images/Select_attach_igw4.png)
attach internet getway

## step 4 - create NAT getway 
while creating nat getway --> create it in public subnet so that internet flow 
![step 4](../images/Create_nat1.png)
## while creating NAT getway allocate Elastic iP
![step 4](../images/Create_nat2.png)

## step 5 - public route table
edit route table 
![step 5](../images/Public_RT1.png)
edit routes in public route table 
![step 5](../images/Edit_routes2.png)
create entry of IGW in route table 
![step 5](../images/IGW_entry3.png)
edit subnet association 
![step 5](../images/Edit_subnet_association4.png)
Give entry of public subnet in Route table 
![step 5](../images/public_subnet_associated.png)

## step 6 - private route table 
create private route table
![step 6](../images/Create_pvt_rt1.png)
edit routes in private route table 
![step 6](../images/Edit_routes_pvt_rt2.png)
add an entry of NAT getway in private route table
![step 6](../images/NAT_getway_entry_rt3.png)
eddit subnet association in private route table 
![step 6](../images/pvt_subnet_associate_rt4.png)
.
![step 6](../images/rt_associated_rt5.png)

# check resource map 
## public 
![check](../images/Public_resource_map.png)
## private 
![check](../images/Private_resource_map.png)


## step 7 - create public ec2 instance in public subnet [lab-1](../lab-1) 

## step 8 - create private ec2 instance in private subnet 
change in network section while creating private ec2 | public ipv4 -> disabale
![private_ec2](../images/Network_pvt_subnet.png)

## ssh into private Ec2
check for private instance ipv4 (private ipv4)
![private_instance](../images/private_ip.png)
copy the keypair.pem in public ec2 to take ssh and follow the command given below 
![private_instance](../images/steps_to_pvt_acess.png)

![ssh](../images/Private_instance_ec2.png)


