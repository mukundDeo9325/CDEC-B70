## linux revise
```bash 
## **Introduction to DevOps**

* DevOps means **Development + Operations** working together.
* Goal is to improve **software delivery speed**, **quality**, and **automation**.
* Removes communication gap between developer and operations teams.
* Focus Areas:

  * Collaboration
  * CI/CD (Continuous Integration & Continuous Delivery)
  * Automation
  * Monitoring
  * Continuous Improvement

---

## **What is an Application?**

* A software created to solve a **specific problem**.
* Examples:

  * WhatsApp → Messaging
  * Swiggy → Food delivery
* Main Components:

  * **Frontend**: User interface
  * **Backend**: Logic and processing
  * **Database**: Stores data

---

## **Developers vs Testers vs DevOps**

| Role            | Responsibility                              |
| --------------- | ------------------------------------------- |
| Developer       | Writes code based on requirements           |
| Tester          | Checks application for issues/bugs          |
| DevOps Engineer | Deploys, automates, and manages environment |

**DevOps acts as a bridge between Dev & Ops.**

---

## **Top Features of Linux**

* Free and Open Source
* Highly Secure and Stable
* Command-line power and flexibility
* Widely used in servers and cloud systems
* Strong community support

---

## **Linux Everywhere**

* Most **cloud servers** run on Linux
* Used in:

  * Data centers
  * Web servers
  * Networking devices
  * Firewalls
  * Supercomputers
* Industry standard for backend infrastructure

---

## **Operating Systems Basics**

* OS is a software that controls **hardware & applications**.
* Examples:

  * Windows
  * Linux (Unix family)
  * macOS
  * Android
  * iOS

---

## **Windows vs Linux**

| Feature       | Windows               | Linux                            |
| ------------- | --------------------- | -------------------------------- |
| Cost          | Paid                  | Free & Open Source               |
| Performance   | Good for Personal Use | Best for Servers and Development |
| Security      | Moderate              | Very Secure                      |
| Interface     | GUI Focused           | CLI + GUI                        |
| Customization | Limited               | Highly Customizable              |

---

## **What is a Server?**

* A computer system that **provides service to multiple users**.
* Always running, powerful hardware.
* Mostly uses **Linux** due to reliability.

---

## **Basic Linux Commands**

| Action                  | Command            |
| ----------------------- | ------------------ |
| Check Current Directory | `pwd`              |
| List Files/Folders      | `ls`               |
| Change Directory        | `cd foldername/`   |
| Create File             | `touch filename`   |
| View File Content       | `cat filename`     |
| Make Directory          | `mkdir foldername` |

---

## **Linux File System Structure**

Everything starts from **root (/)**.

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/home`   | User home directories          |
| `/root`   | Root user home directory       |
| `/etc`    | System configuration files     |
| `/var`    | Logs and variable data         |
| `/bin`    | Essential system commands      |
| `/usr`    | Installed software & libraries |
| `/tmp`    | Temporary files                |
| `/dev`    | Device files                   |  
| `/lib`    | System libraries               |
| `/lib64`  | 64-bit system libraries         |
| `/opt`    | Optional software packages     |
| `/srv`    | Service data                   |
| `/boot`   | Boot loader files              |
| `/mnt`    | Mount points for external drives|
| `/proc`   | Process and kernel information  |
| `/sys`    | System information              |
| `/media`  | Removable media mount points    |
| `/run`    | Runtime variable data           |
| `/sbin`   | System administration binaries  |


---

## **Vim Editor Basics**

* Vim works in different modes:

  * **Command Mode**: Navigation and shortcuts -->esc
  * **Insert Mode**: Typing text (`i` to enter)
  * **Visual Mode**: Selecting text (`v` to enter)
  * **Execute Mode**: Running commands (`:`)-->esc-->:

**Useful Keys:**

* Enter Insert Mode → `i`
* Save File → `:w`
* Quit → `:q`
* Save & Quit → `:wq`
* Undo → `u`
* Redo → `Ctrl + r`
* Delete Line → `dd`
* Copy Line → `yy`
* Paste Line → `p`
* Search → `/text`
* Replace → `:%s/old/new/g`
* remove line numbers --> :set nonu
* set line numbers --> :set nu


## commands 
cd --> change directory
ls --> list files and folders
pwd --> present working directory
mkdir --> make directory (empty)
touch --> create a file / time update a file
rm --> remove file
rmdir --> remove directory(empty)
rm -r --> remove directory (with files)
rm -rvf --> remove directory forcefully (with files)
cp --> copy file
mv --> move file / rename file
cat --> view file content 
tail --> view last 10 lines of file
head --> view first 10 lines of file
du --> disk usage
free --> view memory usage
less --> view large files page by page last 10 lines of file
more --> view large files page by page first 10 lines of file

```
- https://www.redhat.com/en/blog/introduction-vi-editor
- https://www.redhat.com/en/blog/get-started-vi-editor
