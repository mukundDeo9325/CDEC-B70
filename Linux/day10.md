## user and group management

types of users:
* root user (superuser) - has all permissions
* local users - limited permissions
* system users - used by system services

useradd command:
* `sudo useradd username` - create a new user
* `sudo passwd username` - set password for the user
* `sudo usermod -aG groupname username` - add user to a group
* `sudo deluser username` - delete a user  

useradd vs adduser:
* `useradd` is a low-level utility for adding users.
* `adduser` is a more user-friendly script that uses `useradd` in the background. 

groupadd command:
* `sudo groupadd groupname` - create a new group
* `sudo delgroup groupname` - delete a group    
* `sudo usermod -aG groupname username` - add user to a group
* `sudo gpasswd groupname` - add password to group
* `sudo gpasswd -A username groupname` - add group admin
  
viewing users and groups:
* `cat /etc/passwd` - view all users
* `cat /etc/group` - view all groups    

## passwd file structure:
