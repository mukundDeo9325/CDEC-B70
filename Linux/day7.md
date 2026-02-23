## Linux File System 
- https://www.geeksforgeeks.org/linux-unix/linux-file-hierarchy-structure
<img width="708" height="623" alt="image" src="https://github.com/user-attachments/assets/8fa3fd74-2417-46a0-b81f-c4a6f63164f8" />

# Day 6: Delving Deep into the Linux File System

## Mastering the Linux File System Hierarchy
The Linux file system hierarchy is designed to organize files and directories logically and efficiently. Understanding its structure is crucial for navigating and managing the operating system effectively.

### Key Concepts:
- The Linux file system starts at the root directory `/`, which contains all other files and directories.
- Everything in Linux, including hardware devices, is represented as a file.

### Hierarchical Structure:
- **Root (`/`)**: The topmost directory of the Linux file system.
- **Parent and Child Directories**: Directories can contain subdirectories and files, forming a tree-like structure.

## The Significance of the Linux File System Hierarchy
The standardized hierarchy ensures consistency across Linux distributions, making it easier to locate and manage files.

### Benefits:
- Streamlined organization of system and user files.
- Simplifies troubleshooting and system maintenance.
- Facilitates software compatibility across distributions.

## Inside the Linux Root Directory: What You Need to Know
The root directory (`/`) contains several subdirectories, each serving a specific purpose. Here are some key directories:

### Key Directories:
- **`/bin`**: Essential user binaries (e.g., `ls`, `cp`, `mv`).
- **`/boot`**: Boot loader files and kernel images.
- **`/etc`**: Configuration files for the system and applications.
- **`/home`**: User home directories.
- **`/var`**: Variable files such as logs, caches, and temporary files.
- **`/usr`**: User-installed software and libraries.
- **`/dev`**: Device files representing hardware components.
- **`/tmp`**: Temporary files created by applications.
- **`/proc` and `/sys`**: Virtual file systems providing kernel and process information.

### Practical Example:
To explore the root directory, use:
```
ls /
```

## Understanding the Functionality of Common Linux Directories
Each directory in Linux has a specific function. Here is a breakdown of some important ones:

### Common Directories:
- **`/bin` and `/sbin`**:
  - Contain essential system utilities and binaries.
- **`/lib` and `/lib64`**:
  - Shared libraries needed by binaries in `/bin` and `/sbin`.
- **`/opt`**:
  - Optional software packages.
- **`/mnt` and `/media`**:
  - Mount points for external drives and devices.

### Hands-On:
Navigate and inspect the contents of these directories to understand their role:
```
cd /etc
ls -l
```

## Introduction to Linux Shortcuts: Boost Your Efficiency
Linux provides several shortcuts to improve efficiency while navigating the file system and executing commands.

### Common Shortcuts:
- **`~`**: Refers to the current user’s home directory.
- **`.`**: Represents the current directory.
- **`..`**: Represents the parent directory.
- **`/`**: Refers to the root directory.

### Shortcut Examples:
- Navigate to the home directory:
  ```
  cd ~
  ```
- Move up one level in the directory tree:
  ```
  cd ..
  ```
- Combine shortcuts for quick navigation:
  ```
  cd ~/Documents
  ```

### Tips for Efficiency:
- Use **Tab Completion** to auto-complete file and directory names.
- Leverage **`alias`** to create shortcuts for frequently used commands.
  - Example:
  - open file from home dir of user
```
cd
nano .bashrc
```
```
alias ll='ls -l'
alias m='mkdir'
alias s='systemctl'
```
- to run file 
```
source .bashrc
```

