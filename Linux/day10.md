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

---

## Managing Users and Permissions in Linux
- currently user is effective 
  ```
  whoami
  ``` 
- all user list 
  ```
  cat /etc/passwd
  ```

### UID 
```
 root ---> 0 
 local user --> 1000 to 65536+ /home/username
 system user ---> 1 to 999 
```

# adding an user to linux system 
- `adduser <username>` - affect the user related files , crete home dir /home/username , and password permision 
- `useradd <username>` - only add new user to linux system without add home dir to /home, not assing with password 

swich from one user to another 
- `su username` ---> only  root 
- `sudo -i ` ----> to switch to root user only sudo user can switch into root 

## adding new group in linux 
- `groupadd <groupname>`
- adding an user to that group `usermod -aG <groupname> <username>`
- check all the group in wich user is added `groups <username>`
- to check history `history`(show all the command run by that user) ---history is userspecific

---
### Overview of User and Permission Management
# Linux User & Permission Management

---

## Overview of User and Permission Management

Linux is a **multi-user operating system**. Each user has specific permissions to access files and resources.

---

## Types of Users

| User Type | Description |
|---------|-------------|
| Root | Superuser (Admin) |
| Normal User | Regular system user |
| System User | Service accounts |

---

## Creating Users (useradd)

```bash
sudo useradd devuser
```

Create with home directory:

```bash
sudo useradd -m devuser
```

---

## Setting User Password

```bash
sudo passwd devuser
```

---

## Managing Groups

Create group:

```bash
sudo groupadd devops
```

Add user to group:

```bash
sudo usermod -aG devops devuser
```

Check user groups:

```bash
groups devuser
```

---

## Removing Users

```bash
sudo userdel devuser
```

Delete with home:

```bash
sudo userdel -r devuser
```

---

## Important Affected Files

| File | Purpose |
|----|--------|
| `/etc/passwd` | User accounts |
| `/etc/shadow` | Encrypted passwords |
| `/etc/group` | Group details |

---

## User Home Directories

Located at:

```bash
/home/username
```

---

## Switch Between Users

### Using su Command

```bash
su - username
```






