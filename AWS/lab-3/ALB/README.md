# Application load balancer 
https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html
A load balancer serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. This increases the availability of your application. You add one or more listeners to your load balancer.

# steps to create an Application load balancer 
## step 1 - Open EC2 → Load Balancers → Create Application Load Balancer, give it a name, set scheme Internet-facing, and keep listener HTTP:80.
![alb](./images/Navigate_to_lb.png)
select ALB
![alb](./images/chose_ALB.png)
Give name and internet facing 
![alb](./images/Basic_info.png)

## step 2 - Select your VPC and choose at least two public subnets in different Availability Zones.
![network](./images/MultiAZ_4.png)

Attach or create a security group that allows inbound HTTP (port 80) from 0.0.0.0/0.
![sg](./images/SG_allow_http_5.png)

## step 3 - Create a new Target Group [lab-3/target](../Target)
![select_TG](./images/Home_TG.png)
create Load balancer 

## step 4 - Register and add your EC2 instances to the target group.
![target](../Target/images/ALB_LB_homeTG.png)
![target](../Target/images/Register_TG_include_as_pending_4.png)

## step 5 - Register and add your EC2 instances to the target group /mobile/
Add rule --> mobile target group 
![mobile](./images/ALB_LB_rule.png)
path based routing 
![path_mobile](./images/Add_rule_path_forward_tg.png)

## step 6 - check all the EC2 instances 
![check](./images/Check_all_EC2.png)

## step 7 - Create the ALB and test using its DNS URL in a browser.
![dns](./images/ALB_LB_DNS.png)
copy and check in browser 
![browser](./images/ALB_LB_DNS_home.png)
![browser](./images/Home_backup.png)
### path based routing in ALB 
![browser](./images/Path_base_routing.png)







