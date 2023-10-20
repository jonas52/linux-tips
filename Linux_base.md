# Commande de base sur Linux
- **Document réaliser par Jonas Petitpierre**

- [**Networking**](#Networking)
- [**Security**](#Security)
- [**Packages**](#Packages)
- [**Files**](#Packages)
- [**System**](#Security)
- [**Hardware Information**](#Hardware-Information)
- [**Users**](#Users)
- [**File Permission**](#File-Permission)
- [**Keyboard Shortcuts**](#Keyboard-Shortcuts)
- [**Environment Variable Commands**](#Environment-Variable-Commands)

## Networking
----
### Get the IP address of all interfaces
```
networkctl status
```
### Display all IP addresses of the host
```
hostname -I
```
### show IP addresses and network interfaces
```
ip addr show
```
### assign an IP address to interface eth0
```
ip address add
[IP_address]
```
### show IP addresses of all network interfaces
```
ifconfig
```
### show active (listening) ports
```
netstat -pnltu 
```
### show tcp and udp ports and their programs
```
netstat -nutlp
```
### show more information about a domain
```
whois [domain]
```
### show DNS information about a domain
```
dig [domain]
```
### reverse lookup on domain
```
dig -x host
```
### dig -x [ip_address]
```
reverse lookup of an IP address
```
### do an IP lookup for a domain
```
host [domain]
```
### download a file from a domain
```
wget [file_name]
```
### Enable/disable interface
```
ip link set <interface> up
ip link set <interface> down
```
### Show routes
```
ip route
```
### Which route will be used to reach a host
```
ip route get <IP>
```
### List open ports and associated processes
```
sudo ss -tulpn
```
### Manage firewall rules
```
Enable firewall: sudo ufw enable
List rules: sudo ufw status
Allow port: sudo ufw allow <port>
Deny port: sudo ufw deny <port>
Disable firewall: sudo ufw disable
```
### Connect remotely through SSH
```
ssh <user>@<host IP>
```
## Security
----
### Show which users are logged in
```
w
```
### Get user password expiration date
```
chage -l <user>
```
### Set user password expiration date
```
chage <user>
```
### Lock a user account
```
sudo passwd -l <user>
```
### Unlock a user password
```
sudo passwd -u <user>
```
### Automatically detect and ban abusive IP addresses
```
sudo apt install fail2ban
```
### Show banned IP addresses
```
sudo fail2ban-client status
sudo fail2ban-client status <jail>
```
## Packages
----
### Search for packages
```
apt search <string>
snap find <string>
```
### List available package versions
```
apt-cache policy <package>
```
### List available updates
```
apt list --upgradable
```
### Apply all available updates
```
sudo apt update && sudo apt upgrade
```
### Install from the Ubuntu Archive:
```
sudo apt install <package>
```
### Install from the Snap Store:
```
sudo snap install <package>
```
### Remove the package
```
sudo apt remove <package>
```
### Remove the package
```
sudo snap remove <package>
```
### Remove the package and all its configuration files
```
sudo apt purge <package>
```
### Reinstall broken package
```
sudo apt install -f --reinstall
<package>
```
### Which files does this package provide?
```
dpkg-query -L <package>
```
### Which package provides this file?
```
dpkg-query -S <path>
```
## Files
----
### list files in directory
```
ls
```
### list all files, including hidden
```
ls -al
```
### Open a file (or create new one) in nano text editor
```
nano file
```
### Open a file (or create new one) in vim text editor
```
vim file
```
### cat file
```
cat file
```
### show the directory currently working in
```
pwd
```
### compares two files’ content and their differences.
```
diff 
```
### displays a file’s first ten lines.
```
head 
```
### file 
```
file 
```
### create a new directory
```
mkdir [directory]
```
### remove a file
```
rm [file_name]
```
### remove a directory recursively
```
rm -r [directory_name]
```
### remove a directory recursively without requiring confirmation
```
rm -rf [directory_name]
```
### copy the contents of the first file to the second file
```
cp [file_name1] [file_name2]
```
### recursively copy the contents of the first directory into the second directory
```
cp -r [directory_name1] [directory_name2]
```
### rename file_name1 to file_name2
```
mv [file_name1] [file_name2]
or 
rename [file_name1] [file_name2]
```
### create a symbolic link to a file
```
ln -s /path/to/[file_name] [link_name]
```
### encrypt a file
```
gpg -c [file_name]
```
### decrypt a file
```
gpg [file_name.gpg]
```
### print the number of words, lines,
and bytes in a file
```
wc
```
### Common file operations
```
create empty: touch <filename>
create with size: fallocate -l <size>
<filename>
create with content: echo "<content>" >
<filename>
```
### Quick file search
```
locate <filename>
```
### Search string in file
```
grep <string> <filename>
```
### Search string recursively in directory
```
grep -Iris <string> <directory>
```
### Find files modified in the last <n> minutes
```
find <directory> -mmin -<n> -type
f
eg. find . -mmin -5 -type f
```
### Show only the nth column
```
col<n> “<separator>” <filename>
eg. col2 “,” foo.csv
```
### Display file paginated
```
less <filename>
```
### Display first <n> lines
```
head -n <n> <filename>
```
### Display last <n> lines
```
tail -n <n> <filename>
```
### Follow file content as it increases
```
tail -f <filename>
```
### Pack a directory into an archive
```
tar.gz: tar cvzf <target>.tar.gz
<source dir>
zip: zip -r <target> <source dir>
```
### Unpack an archive
```
tar.gz: tar xf <tar.gz file>
zip: unzip <zip file>
```
### Copy file to remote server
```
rsync <filename> <user@
server>:<destination>
eg. rsync config.yaml
admin@192.0.0.0:/config
```
### Copy directory recursively from remote server
```
rsync -avruz <user@
server>:<source> <destination>
eg. rsync -avruz admin@192.0.0.0:/
config /tmp
```
## System
----
### show system information
```
uname -ar
```
### Reboot the system
```
reboot
```
### Shut down the system
```
poweroff
```
### show a snapshot of active processes
```
ps
```
### shows a command’s manual.
```
man
```
### lists previously run commands.
```
history 
```
### manages system services.
```
systemctl 
``` 
### show processes as a tree
```
pstree
```
### shows a memory usage map of processes
```
pmap
```
### show all running processes
```
top
```
### kill all processes labelled proc
```
killall [proc_name]
```
### list and resume stopped jobs in the background
```
bg
```
### list files opened by processes
```
lsof
```
### show how long the system has been running, including load average
```
uptime
```
### show system hostname
```
hostname
```
### show the IP address of the system
```
hostname -i
```
### show system reboot history
```
last reboot
```
### show current time and date
```
date
```
### query and change the system clock
```
timedatectl
```
### show current calender month and day
```
cal
```
### Get root disk usage
```
df -h
```
### Get memory usage
```
cat /proc/meminfo
```
### Get system time
```
timedatectl status
```
### Set system timezone
```
timedatectl list-timezones
sudo timedatectl set-timezone <zone>
```
### connexion db mysql
```
mysql -u root -p
```
### displays the status of a service
```
systemctl status <service>
```
### Get all running/failing services
```
systemctl --state running
systemctl --state failed
```
### Start, stop or restart a service
```
systemctl start/stop/restart <service>
```
### Get the full content of a systemd unit including overrides
```
systemctl cat <service>
```
### Edit a systemd avoiding conflicts with package updates
```
systemctl edit <service>
```
### Monitor new logs for a service
```
journalctl -u <service> --since now -f
```
### Monitor all logs since boot
```
journalctl --boot 0
```
### Get the list of recent logins
```
last
```
### Display running processes
```
htop
```
### Kill process by id
```
kill <process id>
```
### Kill process by name
```
pkill <process name>
```
### Run command in the background
```
<command> &
# staying alive after hangup and logging to file
nohup <command> >> /var/log/yourcommand.log 2>&1 &
```
### Display background commands
```
jobs
```
### Bring command <n> to the foreground
```
fg <n>
```
## Hardware Information
----
### show bootup messages
```
dmesg
```
### show free and used space on mounted systems
```
df -h
```
### show free inodes on mounted filesystems
```
df -i
```
### show disk partitions, sizes, and types
```
fdisk -l
```
### show disk usage for all files and directory
```
du -ah
```
### show disk usage of current directory
```
du -sh
```
### show target mount point for all filesystems
```
findmnt
```
### mount a device
```
mount [device_path] [mount_point]
```
### show CPU information
```
cat /proc/cpuinfo
```
### show free and used memory (-m flag indicates memory in MB)
```
free -h
```
### list information about hardware configuration
```
lshw
```
### list information about block devices
```
lsblk
```
### show PCI devices in a tree-like diagram
```
lspci -tv
```
### show USB devices in a tree-like diagram
```
lsusb -tv
```
### show hardware information from the BIOS
```
dmidecode
```
### show information about disk data
```
hdparm -i /dev/[disk]
```
### conduct a read speed test on disk
```
hdparm -tT /dev/[disk]
```
### test for unreadable blocks on disk
```
badblocks -s /dev/[disk]
```
### See general information about host bridge, VGA controller, ethernet controller, USB controller, SATA controller, etc.
```
lspci
```
### See some information about BIOS, motherboard, chassis, etc.
```
dmidecode	
```
### Retrieve processor type, socket, speed, configured flags, etc.
```
cat /proc/cpuinfo	
```
### See information about the CPU
```
x86info or x86info -a	
```
### See detailed information about system RAM
```
cat /proc/meminfo
```
### List all hardware components and see their configuration details

```
lshw	
```
### Detect number of RAM slots used, speed, and size
```
lshw -C memory -short	
```
### List details for all hardware, including their device files and configuration options
```
hwinfo
```
### Get some general information about your system’s BIOS
```
biosdecode
```
### Retrieve the name of your BIOS vendor with this simple command
```
dmidecode -s bios-vendor	
```
### Get a list of USB devices plugged into your system
```
lsusb	
```
### Retrieve a list of USB device files
```
ls -la /dev/disk/by-id/usb-*	
```
### Retrieve a list of USB device files
```
hdparm -I /dev/sdx	
```
### Show the speed of an installed hard drive – including cached reads and buffered disk reads
```
hdparm -tT /dev/sdx
```
### wodim --devices	
```
Locate CD or DVD device file
```
## Users
----
### show user you are using
```
whoami
```
### show information about a user
```
finger[username]
```
### show details of the active user
```
id
```
### show the last logins onto the system
```
last
```
### show who is logged into the system
```
who
```
### show who is logged in and their activity
```
w
```
### add a new group
```
groupadd [group_name]
```
### add new user
```
adduser [user_name]
```
### add a user to a group
```
usermod -aG [group_name] [user_name]
```
### add a user sudo
```
sudo usermod -a -G sudo user
```
### delete a user
```
userdel [user_name]
```
### use for changing / modifying user information
```
usermod
```
### Switch to another user account.
```
su username
```
### Set or change the password for a user account.
```
passwd username
```
## File Permission
----

### The user (owner) of the file can change its permissions with the command
```
chmod {ugo}{+-=}{rwx} <files>
```
### give read, write, and execute permission to everyone
```
chmod 777 [file_name]
```
### give full permission to owner, and read and execute permission to group and others
```
chmod 755 [file_name]
```
### give full permission to owner, and read and write permission to group and others
```
chmod 766 [file_name]
```
### change the file ownership
```
chown [user] [file_name]
```
### change the owner and group
connect to host as user ownership of a file
```
chown [user]: [group] [file_name]
```
## Keyboard Shortcuts
----
### kill current process running in the terminal
```
Ctrl + C
```
### stop current process (can be resumed in the foreground with fg or in the background with bg)
```
Ctrl + Z
```
### cut one word before the cursor and add it to clipboard
```
Ctrl + W
```
### cut part of the line before the cursor and add it to clipboard
```
Ctrl + U
```
### cut part of the line after the cursor and add it to clipboard
```
Ctrl + K
```
### paste from clipboard
```
Ctrl + Y
```
### recall last command that matches the provided characters
```
Ctrl + R
```
### run the previously recalled command
```
Ctrl + O
```
### exit command history without running a command
```
Ctrl + G
```
### repeat the last command
```
!!
```
### log out of current session
```
exit
```
## Environment Variable Commands
### List all environment variables on a Linux system, or a specific one
```
printenv or printenv variable_name
```
### Find where a command in PATH is located
```
whereis and which
```
### Set a temporary environment variable (just an example, but use the same syntax)
```
export MY_SITE="linuxconfig.org"
```
### echo $VARIABLE
```
echo $VARIABLE
```
### Remove a variable
```
unset
```
   
###### ne pas toucher ça:
###
```
```