## CLB (Clasic Load Balancer)
A load balancer distributes incoming application traffic across multiple EC2 instances in multiple Availability Zones. This increases the fault tolerance of your applications. Elastic Load Balancing detects unhealthy instances and routes traffic only to healthy instances.
https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/introduction.html

# steps to create an classic load balancer 
## step 1 - navigate to load balancer in EC2 service & chose CLB 
![clb_navigate](./images/Navigate_to_lb1.png)
.
![clb_chose](./images/chose_LB2.png)

## step 2 - check basic configuration as name and internet facing you are using it expose application 
![basic](./images/CLB_3.png)

## step 3 - network maping chose AZ (multi az to balance load) & sequrity 
![networking](./images/Network_sub5.png)
![networking](./images/configure_sequrity6.png)

## step 4 - check for lisner port and health check / 
![port](./images/lisner_port7.png)
![port](./images/Health_check8.png)

## step 5 - review settings
![settings_review](./images/Review_settings9.png)

## step 6 - manage instance for load balancing & and chose instances  
lanch ec2 instance [lab-1](../../lab-1)
![load_balancer](./images/manage_instance.png)
![load_balancer](./images/select_instances.png)

## step 7 - copy DNS and check in browser weather instance hitting differet server for balancing load 
![DNS_load](./images/copy_DNS_tocheck.png)
server dns
![DNS_load](./images/Server1.png)
.
![DNS_load](./images/Server2.png)

