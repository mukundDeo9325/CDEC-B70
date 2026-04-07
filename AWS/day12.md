## vpc pearing connection [vpc](./VPC)
<img width="838" height="507" alt="Screenshot 2026-01-21 at 4 01 45 PM" src="https://github.com/user-attachments/assets/f6bfc5e7-2b60-44cb-8bb1-82b75bc163c5" />

## NIC --> PRIVATE IP 
## Elastic IP ---> Static ip Address --> instance ip same 

## placement group and SG vs NACL 
--- 
## Elastic IP
An Elastic IP address is a static, public IPv4 address designed for dynamic cloud computing. It is associated with your AWS account and can be easily remapped to any instance in your account, allowing you to maintain a consistent IP address even if you stop and start your instances.

## Placement Group!
<img width="1013" height="606" alt="Screenshot 2026-01-21 at 3 47 02 PM" src="https://github.com/user-attachments/assets/8dc59f4b-95f9-4e0f-8073-dfbc570617f7" />
<img width="760" height="411" alt="Screenshot 2026-01-21 at 3 50 36 PM" src="https://github.com/user-attachments/assets/b7e7f9ce-d25e-4513-87b3-27d1b6b90a3f" />

A placement group is a logical grouping of instances within a single Availability Zone. Placement groups are used to meet the needs of applications that benefit from low network latency, high throughput, or both. There are two types of placement groups: cluster placement groups and spread placement groups.

## NACL vs SG!
<img width="754" height="584" alt="Screenshot 2026-01-21 at 3 47 33 PM" src="https://github.com/user-attachments/assets/000ded84-c694-4ed1-81a8-6796fd52d45d" />

Network Access Control Lists (NACLs) and Security Groups (SGs) are both used to control traffic to and from AWS resources, but they operate at different levels and have different use cases.

- **NACLs** are stateless, meaning that they evaluate traffic in both directions (inbound and outbound) separately. They are applied at the subnet level and can be used to allow or deny traffic based on IP addresses, protocols, and ports.

- **Security Groups**, on the other hand, are stateful. This means that if you allow an inbound request from a specific IP address, the response is automatically allowed, regardless of outbound rules. Security Groups are applied at the instance level and are typically used to control access to specific resources.
