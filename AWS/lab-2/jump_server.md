A Jump Server (also called a Bastion Host) in AWS is a secure entry point that allows you to connect to your private EC2 instances
get a private server ssh in public server 


steps: 
creat an isolated vpc and creat an two subnet 

public_subnet --> IGW --> public ip enable
Route table --> edit routes--> IGW enty ; subnet association public subnet 

private subnet --> Nat(public)--> disable public ip 
route table --> edit routes--> nat entry ; subnet associate private subnet 

lanch ec2 instance with both subnets:-

public instance --> public ip enable chose public subnet 

private instance --> public ip desebal chose private subnet 

take ssh of public instance --> copy key --> key.pem --> chmod 400(to sequare key)key.pem
--> ssh -i key.pem os_name@private_ip

ex: ssh -i key.pem ubuntu@172.168.0.0

---------------------------------------------------------------------------------------------
