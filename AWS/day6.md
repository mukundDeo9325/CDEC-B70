## Aws storage types 
- Block Storage --> EBS (Elastic Block Store)
- Object Storage --> S3 (Simple Storage Service)
- Network File System --> EFS (Elastic File System) (shared storage)
- https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html


## EBS (Elastic Block Store)

SSD 
- General Purpose SSD (gp2, gp3)
- Provisioned IOPS SSD (io1, io2)   

HDD
- Throughput Optimized HDD (st1)    
- Cold HDD (sc1)

Magnetic (Standard)  (previous generation)




```
what are the storage types in AWS?
what are the types of EBS volumes?

```


EBS Volume Mount steps:
1. Create EBS volume in the same AZ as EC2 instance
2. Attach EBS volume to EC2 instance
3. Connect to EC2 instance using SSH
4. List block devices using `lsblk` command
5. Create a file system on the EBS volume using `mkfs` command
6. Create a mount point using `mkdir` command
7. Mount the EBS volume to the mount point using `mount` command
8. Update `/etc/fstab` file to mount the EBS volume at boot time

```bash 
 sudo fdisk /dev/nvme1n1.  ## to create partition
       n--> new partition
       p--> primary
       1--> partition number
       <DEFAULT> --> default first sector
       <+2G> --> default last sector
        W --> write and exit

 sudo mkfs.ext4 /dev/nvme1n1  1  ## to create filesystem
 sudo mkdir data  ## to create mount point
 sudo mount /dev/nvme1n1p1 data  ## to mount volume
``` 
--- 
### new instance 
- attach volume to ec2 instance
- volume --> select volume ---> action ---> attach volume 
```bash
mkdir test   ## crete directory to attach volume 
sudo mount /dev/nvme1n1p1 test   ## mount volume 
```
