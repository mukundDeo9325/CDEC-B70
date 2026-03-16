## AWS Dashboard
## Region
- AWS regions are separate geographic areas that has clusters of data centers.
- Each region is completely independent and isolated from other regions.
- AWS has multiple regions around the world, allowing users to deploy applications in locations that are closer to their end-users.

## Availability Zones
- Availability Zones (AZs) are isolated locations within a region.
- Each region has multiple AZs, which are designed to be independent from each other.
- AZs provide high availability and fault tolerance for applications by allowing users to distribute their resources across multiple locations.

## ec2 instance lasuching steps
1. Login to AWS Management Console.
2. Navigate to the EC2 Dashboard.
3. Click on "Launch Instance" button.
4. Choose an Amazon Machine Image (AMI) that suits your needs.
5. Select an instance type based on your requirements for CPU, memory, and storage.
6. Configure instance details such as the number of instances, network settings, and IAM roles.
7. Add storage volumes if needed.
8. Add tags to help identify and manage your instance.
9. Configure security group settings to control inbound and outbound traffic.
10. Review your instance configuration and click "Launch".
11. Select or create a key pair for SSH access to your instance.
12. Click "Launch Instances" to start your EC2 instance.

## Key Pair
- A key pair consists of a public key and a private key.
- The public key is stored on the EC2 instance, while the private key is kept by the user.
- Key pairs are used for secure SSH access to EC2 instances.

## Security Groups
- Security groups act as virtual firewalls for your EC2 instances.
- They control inbound and outbound traffic to and from your instances.
- You can define rules to allow or deny specific types of traffic based on protocols, ports,

```
what is EC2?
what is Region?
what is Availability Zone?
```
