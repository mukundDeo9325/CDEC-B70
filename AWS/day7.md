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
/dev/xvdf1  /mnt/ebs  ext4  default 0 0    
```
- mkfs -t ext4 /dev/xvdf1   #to format partition with ext4 file system
- mount -a   #to mount all file systems mentioned in fstab file


