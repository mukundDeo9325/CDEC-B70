# Target Group 
https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html

Target groups route requests to individual registered targets, such as EC2 instances, using the protocol and port number that you specify. You can register a target with multiple target groups. You can configure health checks on a per target group basis. Health checks are performed on all targets registered to a target group that is specified in a listener rule for your load balancer.


## steps to create Target Group

## step 1 - navigate to target group in EC2 service 
![Target_group](./images/Navigate_to_TG1.png)
Give name to Target Group:
![Target_group](./images/NameTG_2.png)

## step 2 - give Health check Path /your_index.html and NEXT
![health_check](./images/Health_TG3.png)

## step 3 - Register targets and Review & create
![register_target](./images/Register_TG_include_as_pending_4.png)
.
![review](./images/Create_TG5.png)
create target group

## step 4 - check for target gruop 
![check](./images/Final_check_TG_6.png)

