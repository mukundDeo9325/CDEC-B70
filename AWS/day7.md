## Permenant mounting 
```
lsblk ## to check volume is attached or not
fdisk /dev/nvme1n1
  n
  p
  +5G
  w
mkdir /data
mkfs.ext4 /dev/nvme1n1p1  ## attached file system 
lsbk
blkid  /dev/nvme1n1p1 ## label
nano /etc/fstab ## entry uuid /data
mount -a
systemctl daemon-reload
```

## file system and mounting 
https://www.redhat.com/en/blog/partitions-fdisk

## volume mounting and partation 
- lsblk -- list storage
- fdisk /dev/<storage>


# temporary and permenant mounting 
for temporary mounting use
- mount /dev/xvdf1 /mnt/ebs

for permanent mounting
- vim /etc/fstab

`blkid  /dev/nvme1n1p1` ## label

```
UUID=6e8c4021-c063-44d8-b7f6-da090edeedf0  /mnt/server  ext4  defaults,nofail  0  2
```

- nofail: This is critical for AWS EBS volumes. It allows the instance to boot normally even if the volume is detached or fails to mount.
- mkfs -t ext4 /dev/xvdf1   #to format partition with ext4 file system
- mount -a   #to mount all file systems mentioned in fstab file
---
## **Summary**

- **EBS Volumes**: Provide persistent, reliable block storage.
- **Volume Types**: Include SSDs (gp3, gp2, io1, io2), HDDs (st1, sc1), and magnetic storage.
- **Operations**: Attach a volume, create partitions, format, and mount it to an EC2 instance.

```
5th field
0 -  exclude file system backup 
1 -  backup fs everyday 
2 - backup the file system every other day 

6th field 
fs chek for errors during boot process 
0 - exclude fs from fscheck 
1 - check fs during first fscheck 
2 - check fs during second pass of fscheck 
 used for non root fs 

```


