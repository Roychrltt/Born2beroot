# Born2beroot

>sudo adduser <username>

>sudo addgroup <groupname>

>sudo adduser <username> <groupname> (add xiaxu to sudo and user42)

>getent group <groupname> (check if group created successfully)

>groups <username> (to show the groups the user belongs to)

>id <username> (provides more detailed information)

>sudo apt update (update the system)

>sudo apt install openssh-server (install openSSH)

>sudo service ssh status (check if openSSH is active)

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

>sudo service ssh restart (restart the ssh service to update)

>sudo apt install ufw (install UFW)

>sudo ufw enable

>sudo ufw allow 4242 (allow connections that will happen in the 4242 port)

>sudo ufw status

>vi /etc/sudoers.d/sudo_config (create a file to store sudo policy)

To set up sudo policies

>
