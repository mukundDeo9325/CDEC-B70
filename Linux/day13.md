## Archiving and Compressing Files

Archivinng:
- The process of combining multiple files into a single file, often for easier storage or transfer.
tar command:
- `tar -cvf archive_name.tar /path/to/directory_or_files` : Create a tar archive.
- `tar -xvf archive_name.tar` : Extract a tar archive.

Compressing:
- The process of reducing the size of a file or archive to save disk space or reduce transfer time.
- Commonly used tools: `gzip`, `bzip2`, `xz`.
gzip command:
- `gzip filename` : Compress a file, resulting in `filename.gz`.
- `gunzip filename.gz` : Decompress a `.gz` file.

bzip2 command:
- `bzip2 filename` : Compress a file, resulting in `filename.bz2`.
- `bunzip2 filename.bz2` : Decompress a `.bz2` file

xz command:
- `xz filename` : Compress a file, resulting in `filename.xz`.
- `unxz filename.xz` : Decompress a `.xz` file.

tar
- convert tar file to normal file
- `tar -xvf file.tar` conver file in normal file/dir
## cron
![crontab-explanation-1](https://github.com/user-attachments/assets/d2cfe8d0-850c-4dcf-bdcd-2e4d1b10895d)
 jobs

crontab field structure:
* minute (0-59)
* hour (0-23)
* day of month (1-31)
* month (1-12)
* day of week (1-7) (1 or 7 = Sunday) | (0 to 6) 0 - sunday 
* command to be executed

crontab commands:
to install crontab 
update the server 
```bash
sudo apt update -y
```

```bash
sudo apt install cron
```

* `crontab -e` : Edit the crontab file for the current user
* `crontab -l` : List the current user's crontab entries
* `sudo crontab -e` : Edit the crontab file for the root user
* `sudo crontab -l` : List the root user's crontab entries
example cron job to run a script every day at 2am:
```0 2 * * * /path/to/script.sh
```


## to change the edditor in crontab 
- make changes in .bashrc file
```
vim ~/.bashrc
```
```
# Set default editor
export EDITOR=vim
export VISUAL=vim
```
```
source ~/.bashrc
```
