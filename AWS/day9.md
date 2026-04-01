## vpc 
With Amazon Virtual Private Cloud (Amazon VPC), you can launch AWS resources in a logically isolated virtual network that you've defined.
- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html

## private IP ranges 
```
IPv4 Private IP Ranges (RFC 1918) 
Class A: 10.0.0.0 to 10.255.255.255 (CIDR: 10.0.0.0/8)
Class B: 172.16.0.0 to 172.31.255.255 (CIDR: 172.16.0.0/12)
Class C: 192.168.0.0 to 192.168.255.255 (CIDR: 192.168.0.0/16)
```
<img width="685" height="501" alt="Screenshot 2026-02-13 at 4 12 46 PM" src="https://github.com/user-attachments/assets/0d9fe7d5-8b56-4647-9a21-fad6684f803f" />

## vpc - 192.168.0.0/16
- sub1 - 192.168.0.0/21
- sub2 - 192.168.8.0/21 


<img width="507" height="326" alt="image" src="https://github.com/user-attachments/assets/0f54cf16-345c-4743-8cb8-4a39cddca544" />

```
10.0.0.0: Network address.
10.0.0.1: Reserved by AWS for the VPC router.
10.0.0.2: Reserved by AWS. The IP address of the DNS server is the base of the VPC network range plus two. For VPCs with multiple CIDR blocks, the IP address of the DNS server is located in the primary CIDR. We also reserve the base of each subnet range plus two for all CIDR blocks in the VPC. For more information, see Amazon DNS server.
10.0.0.3: Reserved by AWS for future use.
10.0.0.255: Network broadcast address. We do not support broadcast in a VPC, therefore we reserve this address.
```
