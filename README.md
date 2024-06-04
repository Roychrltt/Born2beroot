# Born2beroot

'sudo adduser <username>'

'sudo addgroup <groupname>'

'sudo adduser <username> <groupname>'
(add xiaxu to sudo and user42)

>getent group <groupname>
(check if group created successfully)

>groups <username>
(to show the groups the user belongs to)

>id <username>
(provides more detailed information)

>sudo apt update
(update the system)

>sudo apt install openssh-server
(install openSSH)

>sudo service ssh status
(check if openSSH is active)

The /etc/ssh/sshd_config file is the main configuration file for the OpenSSH server daemon (sshd). This file controls various settings related to how the SSH server operates, such as the port it listens on, authentication methods, and security options.

Uses of /etc/ssh/sshd_config:

1.Changing the SSH Port to enhance security

2.Restricting Root Login to improve security

3.Configuring Authentication Methods

4.Limiting User Access


The /etc/ssh/ssh_config file is the system-wide configuration file for the OpenSSH client. This file contains default settings for all users on the system when they use the ssh command to connect to remote servers. Unlike /etc/ssh/sshd_config, which configures the SSH server, ssh_config is used to configure the SSH client behavior.

Uses of /etc/ssh/ssh_config:

1.Setting Default Options

2.Configuring Specific Hosts

>sudo service ssh restart
(restart the ssh service to update)

>sudo apt install ufw
(install UFW)

>sudo ufw enable

>sudo ufw allow 4242
(allow connections that will happen in the 4242 port)

>sudo ufw status

>vi /etc/sudoers.d/sudo_config
(create a file to store sudo policy)

### To set up a strong password policy

>vi /etc/login.defs
(open this file to set parameters)

>sudo apt install libpam-pwquality

libpam-pwquality is a PAM(Pluggable Authentication Modules) module that helps ensure that users choose strong passwords. 

>vi /etc/pam.d/common-password
(edit this file to set password policies)

### Connecting to SSH

>ssh <user>@localhost -p 4242
(connect via ssh from the machine to the virstual machine)

### Script

>uname -a
(display detailed information about the system)

Like Kernel Name, Node Name, Kernel Release, Kernel Version, Machine, Processor, Hardware Platform, Operating System.

>grep "physical id" /proc/cpuinfo | wc -l
(search for lines containing "physical id" in the file, wourd count and line)

>grep processor /proc/cpuinfo | wc -l

**RAM**

>free --mega | awk '$1 == "Mem:" {print $3}'
(display the amount of used memory in megabytes, print the 3rd filed of lines whose first field is Mem:)

>free --mega | awk '$1 == "Mem:" {print $2}'
(display total memory)

>free --mega | awk '$1 == "Mem:" {printf("(%.2f%%)\n", $3/$2*100)}'
(print the percentage of used memory)

**disk memory**

>df -m | grep "/dev/" | grep -v "/boot" | awk '{memory_use += $3} END {print memory_use}'
(disk filesystem, get lines containing "/dev", excluding lines containing "/boot", add all the 3rd fields and print the sum, showed in Mb)

>df -m | grep "/dev/" | grep -v "/boot" | awk '{memory_result += $2} END {print ("%0.fGb\n"), memory_result/1024}'
(Obtain the total memory space, display in Gb)

>df -m | grep "/dev/" | grep -v "/boot" | awk '{use += $3} {total += $2} END {printf("(%d%%)\n"), use/total*100}'
(get the percentage of used memory)

**CPU usage percentage**

>vmstat | tail -1 | awk '{print $15}'
(virtual machine statistics) (print the 15th word of the last line, which is the available memory usage)

**Last reboot**

>who -b | awk '$1 == "system" {print $3 " " $4}'
(The who command displays information about users who are currently logged in.
The -b option specifically shows the time of the last system boot.)

**LVM active**

>if [ $(lsblk | grep "lvm" | wc -l) -gt 0 ]; then echo yes; else echo no; fi
(lsblk shows information about all block devices (hard drives, SSDs, memories, etc))

**TCP connections**

>ss -ta | grep ESTAB | wc -l
(ss is to show inverstigate sockets, -t to show TCP sockets and -a to show all listening and non-listening sockets)

**Number of users**

>users | wc -w

**Ip adress 1 MAC**

>ip link | grep "link/ether" | awk '{print $2}'

**Number of commands executed in sudo**

>journalctl _COMM=sudo | grep COMMAND | wc -l
(return the number of lines of commands executed by sodu)

### Crontab

>sudo crontab -u root -e
open the default text editor (such as nano or vim) with the contents of the root user's crontab file. If the crontab file does not exist, it will create a new one.

Add the line >*/10 * * * * sh /home/xiaxu/monitoring.sh

### Signature.txt

Shut down our machine, go to the directory where locates out machine, run >shasum machinename.vdi
