## **1. Introduction to Linux**

### **1.1 Linux Distributions Overview**
Linux is an open-source operating system with many different distributions (distros). Red Hat Enterprise Linux (RHEL) is a distribution designed for enterprise use, known for its stability, security, and support. It’s widely used in servers and data centers.

### **1.2 Understanding the Linux File System**
The Linux file system is hierarchical, starting from the root directory (`/`). Here’s an overview of key directories:

- **`/bin`:** Contains essential command binaries like `ls`, `cp`, and `mv`.
- **`/etc`:** Stores configuration files for the system and applications.
- **`/home`:** Each user has a home directory under `/home` (e.g., `/home/username`).
- **`/var`:** Stores variable files such as logs (`/var/log`), databases, and spool files.
- **`/tmp`:** Temporary files are stored here; the directory is often cleared upon reboot.

### **1.3 Basic Command-Line Usage**
The command line is a powerful tool in Linux. Here are some fundamental commands:

- **Listing Files:**
  ```bash
  ls -l /etc
  ```
  The `ls` command lists the contents of a directory. The `-l` flag provides a long listing format, showing file permissions, ownership, size, and modification date.

- **Changing Directories:**
  ```bash
  cd /etc
  ```
  The `cd` command changes the current working directory. For example, `cd /etc` moves you to the `/etc` directory.

- **Printing the Working Directory:**
  ```bash
  pwd
  ```
  The `pwd` command displays the current directory you’re in.

- **Creating a Directory:**
  ```bash
  mkdir /tmp/newdir
  ```
  The `mkdir` command creates a new directory. Here, it creates `newdir` inside `/tmp`.

- **Removing a Directory:**
  ```bash
  rmdir /tmp/newdir
  ```
  The `rmdir` command removes an empty directory.

---

## **2. Installation and Configuration**

### **2.1 Installing Red Hat Enterprise Linux**
During the installation of RHEL, you’ll go through several steps:
- **Language and Keyboard Selection:** Choose your preferred language and keyboard layout.
- **Time Zone Configuration:** Set your system’s time zone.
- **Partitioning:** Decide how to partition the hard drive (e.g., `/`, `/home`, `/var`).
- **Root Password:** You’ll be prompted to set a root password. The root user has administrative privileges.

### **2.2 Boot Process and System Initialization**
Linux boots using GRUB2 (Grand Unified Bootloader). Once GRUB loads the kernel, `systemd` (the system and service manager) takes over, managing the startup of services and daemons.

- **Viewing the Boot Log:**
  ```bash
  journalctl -b
  ```
  This command displays the log messages generated during the current boot. It’s useful for diagnosing boot issues.

### **2.3 Managing Software with YUM/DNF**
YUM and DNF are package managers used to install, update, and remove software packages on RHEL.

- **Installing a Package:**
  ```bash
  yum install httpd
  ```
  This command installs the Apache HTTP server package (`httpd`). Package managers resolve dependencies automatically.

- **Updating All Packages:**
  ```bash
  yum update
  ```
  This command updates all installed packages to the latest versions available in the configured repositories.

- **Removing a Package:**
  ```bash
  yum remove httpd
  ```
  This removes the `httpd` package and any dependencies that are no longer needed.

---

## **3. Command-Line Skills**

### **3.1 File and Directory Management**
Managing files and directories is a fundamental skill:

- **Copying Files:**
  ```bash
  cp /etc/hosts /tmp/hosts.backup
  ```
  This copies the file `/etc/hosts` to `/tmp/hosts.backup`.

- **Moving or Renaming Files:**
  ```bash
  mv /tmp/hosts.backup /etc/hosts.bak
  ```
  This moves or renames `/tmp/hosts.backup` to `/etc/hosts.bak`.

- **Removing Files:**
  ```bash
  rm /etc/hosts.bak
  ```
  This deletes the file `/etc/hosts.bak`.

- **Viewing the Contents of a File:**
  ```bash
  cat /etc/hosts
  ```
  The `cat` command displays the contents of a file.

### **3.2 Text Editors**
Linux provides text editors like `vi` or `nano` to edit files directly from the command line.

- **Editing a File with `vi`:**
  ```bash
  vi /etc/hosts
  ```
  `vi` is a powerful but complex text editor. In `vi`:
  - Press `i` to enter insert mode and start editing.
  - Press `Esc` to return to command mode.
  - Type `:wq` to save and exit.

### **3.3 File Permissions**
Linux file permissions control who can read, write, or execute a file.

- **Changing File Permissions:**
  ```bash
  chmod 755 /path/to/file
  ```
  The `chmod` command changes the permissions of a file. In this case, `755` sets read, write, and execute permissions for the owner, and read and execute permissions for the group and others.

- **Viewing File Permissions:**
  ```bash
  ls -l /path/to/file
  ```
  This shows the file’s permissions, owner, group, size, and modification date.

### **3.4 File Ownership**
Each file has an owner and a group. The `chown` command is used to change the ownership.

- **Changing File Ownership:**
  ```bash
  chown user:group /path/to/file
  ```
  This changes the owner to `user` and the group to `group`.

### **3.5 Searching for Files and Text**
- **Finding Files by Name:**
  ```bash
  find / -name "filename"
  ```
  The `find` command searches for files in a directory hierarchy. Here, it searches the entire system for `filename`.

- **Searching Text within Files:**
  ```bash
  grep "search_text" /path/to/file
  ```
  `grep` searches for a specific string of text within a file. For example, searching for `"search_text"` within a file.

### **3.6 Redirection and Pipes**
- **Redirecting Output to a File:**
  ```bash
  ls -l > output.txt
  ```
  This command lists the files in the current directory and redirects the output to `output.txt`.

- **Appending Output to a File:**
  ```bash
  ls -l >> output.txt
  ```
  This appends the output of the `ls -l` command to `output.txt`.

- **Using Pipes:**
  ```bash
  ls -l | grep "search_text"
  ```
  The pipe (`|`) sends the output of one command to another command. Here, it sends the output of `ls -l` to `grep`, which searches for `"search_text"`.

---

## **4. System Administration Basics**

### **4.1 User and Group Management**
Managing users and groups is essential for controlling access to the system.

- **Creating a User:**
  ```bash
  useradd username
  ```
  This command creates a new user account named `username`.

- **Setting a Password for the User:**
  ```bash
  passwd username
  ```
  This sets a password for `username`.

- **Modifying a User (e.g., Adding to a Group):**
  ```bash
  usermod -aG groupname username
  ```
  The `usermod` command modifies a user account. The `-aG` option adds the user to an existing group (`groupname`).

- **Deleting a User:**
  ```bash
  userdel username
  ```
  This deletes the user `username` from the system.

- **Creating a Group:**
  ```bash
  groupadd groupname
  ```
  This command creates a new group named `groupname`.

- **Viewing User Details:**
  ```bash
  id username
  ```
  This displays the user’s ID, primary group ID, and the groups they belong to.

- **Viewing Group Membership:**
  ```bash
  groups username
  ```
  This shows all the groups that `username` is a member of.

### **4.2 Network Configuration**
Understanding how to configure network settings is crucial for connecting your server to a network.

- **Viewing Network Interfaces:**
  ```bash
  ip a
  ```
  The `ip a` command shows all network interfaces and their IP addresses.

- **Assigning an IP Address Temporarily:**
  ```bash
  ip addr add 192.168.1.100/24 dev eth0
  ```
  This assigns the IP address `192.168.1.100` to the network interface `eth0`.

- **Viewing the Routing Table:**
  ```bash
  ip route show
  ```
  This shows the routing table, which determines how packets are routed to their destinations.

- **Editing Network Configuration Files:**
  ```

bash
  vi /etc/sysconfig/network-scripts/ifcfg-eth0
  ```
  Network interfaces are configured via files in `/etc/sysconfig/network-scripts/`. The `ifcfg-eth0` file contains configuration settings for the `eth0` interface.

- **Restarting the Network Service:**
  ```bash
  systemctl restart network
  ```
  This command restarts the network service, applying any changes made to the network configuration.

### **4.3 Managing Services**
Services (or daemons) are programs that run in the background, such as web servers, database servers, and more.

- **Starting a Service:**
  ```bash
  systemctl start httpd
  ```
  This starts the Apache HTTP server.

- **Stopping a Service:**
  ```bash
  systemctl stop httpd
  ```
  This stops the Apache HTTP server.

- **Enabling a Service to Start at Boot:**
  ```bash
  systemctl enable httpd
  ```
  This ensures the Apache HTTP server starts automatically at boot.

- **Disabling a Service:**
  ```bash
  systemctl disable httpd
  ```
  This prevents the Apache HTTP server from starting at boot.

- **Checking the Status of a Service:**
  ```bash
  systemctl status httpd
  ```
  This shows the current status of the Apache HTTP server, whether it’s running, and any errors if it failed to start.

### **4.4 SELinux**
SELinux (Security-Enhanced Linux) is a security module that provides a mechanism for supporting access control policies.

- **Checking SELinux Status:**
  ```bash
  sestatus
  ```
  This command shows whether SELinux is enabled, and if so, in which mode (enforcing, permissive, or disabled).

- **Setting SELinux to Permissive Mode:**
  ```bash
  setenforce 0
  ```
  This temporarily sets SELinux to permissive mode, where violations are logged but not enforced.

- **Changing SELinux Mode Permanently:**
  ```bash
  vi /etc/selinux/config
  ```
  Modify the `SELINUX` line in the config file to either `enforcing`, `permissive`, or `disabled` to make the change permanent. After modifying, reboot the system to apply the changes.

### **4.5 Package Management**
Efficiently managing software packages is vital for maintaining the system.

- **Searching for a Package:**
  ```bash
  yum search package_name
  ```
  This searches the repository for packages related to `package_name`.

- **Listing Package Information:**
  ```bash
  yum info package_name
  ```
  This provides detailed information about the specified package, including its version, size, repository, and a description.

---

## **5. Storage Management**

### **5.1 Managing Physical Storage**
Physical storage management involves creating, modifying, and managing disk partitions.

- **Viewing Disk Partitions:**
  ```bash
  fdisk -l
  ```
  This command lists all disk partitions on the system. It’s helpful for identifying existing partitions and their sizes.

- **Creating a New Partition:**
  ```bash
  fdisk /dev/sda
  ```
  This opens the `fdisk` utility for the `/dev/sda` disk, where you can create, delete, or modify partitions interactively. After creating a partition, you typically need to format it and assign a file system.

- **Formatting a Partition:**
  ```bash
  mkfs.ext4 /dev/sda1
  ```
  The `mkfs.ext4` command formats the `/dev/sda1` partition with the EXT4 file system.

- **Mounting a Filesystem:**
  ```bash
  mount /dev/sda1 /mnt
  ```
  This command mounts the `/dev/sda1` partition to the `/mnt` directory, making it accessible.

- **Viewing Mounted Filesystems:**
  ```bash
  df -h
  ```
  The `df -h` command displays the disk space usage of all mounted filesystems, with the `-h` option providing human-readable sizes (e.g., MB, GB).

### **5.2 Logical Volume Management (LVM)**
LVM allows for more flexible management of disk space by abstracting physical disks into logical volumes.

- **Creating a Physical Volume:**
  ```bash
  pvcreate /dev/sdb1
  ```
  The `pvcreate` command initializes a disk partition (e.g., `/dev/sdb1`) as a physical volume for use with LVM.

- **Creating a Volume Group:**
  ```bash
  vgcreate myvg /dev/sdb1
  ```
  The `vgcreate` command creates a volume group named `myvg` from the physical volume `/dev/sdb1`.

- **Creating a Logical Volume:**
  ```bash
  lvcreate -L 10G -n mylv myvg
  ```
  The `lvcreate` command creates a logical volume named `mylv` of size 10GB within the `myvg` volume group.

- **Formatting the Logical Volume:**
  ```bash
  mkfs.ext4 /dev/myvg/mylv
  ```
  This formats the logical volume `/dev/myvg/mylv` with the EXT4 file system.

- **Mounting the Logical Volume:**
  ```bash
  mount /dev/myvg/mylv /mnt
  ```
  This mounts the logical volume to the `/mnt` directory.

### **5.3 Managing Swap Space**
Swap space is used as virtual memory when the physical RAM is fully utilized.

- **Creating a Swap File:**
  ```bash
  dd if=/dev/zero of=/swapfile bs=1G count=1
  ```
  The `dd` command creates a 1GB file named `/swapfile` filled with zeros. This file will be used as swap space.

- **Setting Up the Swap File:**
  ```bash
  mkswap /swapfile
  swapon /swapfile
  ```
  `mkswap` sets up the file as a swap area, and `swapon` enables it as active swap space.

- **Making Swap Space Permanent:**
  ```bash
  echo "/swapfile swap swap defaults 0 0" >> /etc/fstab
  ```
  This adds an entry to the `/etc/fstab` file, ensuring the swap file is activated on boot.

---

## **6. Security**

### **6.1 Configuring the Firewall**
Firewalls control incoming and outgoing network traffic based on security rules.

- **Checking Firewall Status:**
  ```bash
  firewall-cmd --state
  ```
  This command checks if the firewall is running.

- **Allowing a Service Through the Firewall:**
  ```bash
  firewall-cmd --permanent --add-service=http
  firewall-cmd --reload
  ```
  This permanently allows HTTP traffic through the firewall. The `--reload` command applies the changes without interrupting existing connections.

- **Blocking a Service:**
  ```bash
  firewall-cmd --permanent --remove-service=http
  firewall-cmd --reload
  ```
  This blocks HTTP traffic by removing the rule from the firewall.

- **Allowing a Specific Port:**
  ```bash
  firewall-cmd --permanent --add-port=8080/tcp
  firewall-cmd --reload
  ```
  This command allows traffic on TCP port 8080.

### **6.2 Managing SSH**
SSH (Secure Shell) is a protocol for securely connecting to remote systems.

- **Securing SSH by Disabling Root Login:**
  ```bash
  vi /etc/ssh/sshd_config
  ```
  Find the line `PermitRootLogin yes` and change it to `PermitRootLogin no` to prevent direct root login via SSH. After editing the file, restart the SSH service:
  ```bash
  systemctl restart sshd
  ```

- **Changing the SSH Default Port:**
  ```bash
  vi /etc/ssh/sshd_config
  ```
  Change the line `Port 22` to another port number (e.g., `Port 2222`). This adds a layer of security by making it harder for attackers to find the SSH service. Don’t forget to allow the new port through the firewall:
  ```bash
  firewall-cmd --permanent --add-port=2222/tcp
  firewall-cmd --reload
  systemctl restart sshd
  ```

### **6.3 Configuring Sudo**
Sudo allows a permitted user to execute commands as the root user or another user.

- **Allowing a User to Use Sudo:**
  ```bash
  usermod -aG wheel username
  ```
  The `usermod -aG wheel` command adds `username` to the `wheel` group, granting them sudo privileges.

- **Editing the Sudoers File:**
  ```bash
  visudo
  ```
  This command opens the sudoers file in a safe manner, preventing syntax errors that could lock users out of sudo. The file is where you define who has sudo privileges and under what conditions.

---

## **7. System Monitoring and Performance Tuning**

### **7.1 Monitoring System Performance**
Monitoring your system’s performance helps ensure it’s running optimally.

- **Monitoring Processes with `top`:**
  ```bash
  top
  ```
  `top` displays real-time system statistics, including CPU usage, memory usage, and the processes consuming the most resources. Press `q` to exit.

- **Viewing System Load with `uptime`:**
  ```bash
  uptime
 

 ```
  This command shows how long the system has been running and the average system load over the last 1, 5, and 15 minutes. A high load number may indicate the system is overloaded.

- **Memory Usage with `free`:**
  ```bash
  free -h
  ```
  `free` provides a snapshot of the system’s memory usage, including total memory, used memory, and free memory. The `-h` option displays the information in a human-readable format (e.g., MB, GB).

- **Disk I/O Statistics with `iostat`:**
  ```bash
  iostat
  ```
  `iostat` reports on CPU and I/O statistics for devices and partitions, helping you identify bottlenecks related to disk performance.

- **Checking Disk Usage:**
  ```bash
  df -h
  ```
  `df -h` displays disk usage statistics for all mounted filesystems, including the total size, used space, and available space.

### **7.2 Configuring Logging**
Logs are crucial for monitoring system activities and troubleshooting issues.

- **Viewing System Logs:**
  ```bash
  tail -f /var/log/messages
  ```
  `tail -f` displays the last few lines of a log file and continues to display new lines as they are added. This is useful for real-time monitoring.

- **Viewing Journal Logs:**
  ```bash
  journalctl -xe
  ```
  `journalctl` provides access to the systemd journal, which contains logs from the kernel, system services, and applications. The `-xe` options display the most recent logs with detailed explanations.

- **Configuring rsyslog:**
  ```bash
  vi /etc/rsyslog.conf
  ```
  The `rsyslog` service is responsible for logging system messages. You can configure where logs are stored, log rotation, and what gets logged in the `rsyslog.conf` file. After making changes, restart the service:
  ```bash
  systemctl restart rsyslog
  ```

---

## **8. Automation and Scripting**

### **8.1 Writing Basic Shell Scripts**
Shell scripts are a way to automate repetitive tasks by grouping commands into a single executable file.

- **Creating a Script:**
  ```bash
  vi /usr/local/bin/backup_hosts.sh
  ```
  A simple backup script might look like this:
  ```bash
  #!/bin/bash
  cp /etc/hosts /etc/hosts.backup
  ```
  The `#!/bin/bash` line indicates that the script should be executed using the Bash shell.

- **Making the Script Executable:**
  ```bash
  chmod +x /usr/local/bin/backup_hosts.sh
  ```
  The `chmod +x` command makes the script executable. You can now run the script like any other command.

### **8.2 Automating Tasks with Cron**
Cron is a time-based job scheduler that allows you to run scripts or commands at specific times.

- **Scheduling a Cron Job:**
  ```bash
  crontab -e
  ```
  This opens the cron table (crontab) for the current user. You can schedule tasks using the following format:
  ```bash
  0 0 * * * /usr/local/bin/backup_hosts.sh
  ```
  This example runs the `backup_hosts.sh` script every day at midnight.

- **Listing Scheduled Cron Jobs:**
  ```bash
  crontab -l
  ```
  This lists all scheduled cron jobs for the current user.

---

## **9. Network Services**

### **9.1 Configuring a Web Server (Apache)**
Apache is a widely-used web server.

- **Installing Apache:**
  ```bash
  yum install httpd
  ```
  This installs the Apache HTTP server.

- **Starting the Apache Service:**
  ```bash
  systemctl start httpd
  ```
  This starts the Apache service, making the web server available.

- **Enabling Apache to Start on Boot:**
  ```bash
  systemctl enable httpd
  ```
  This ensures Apache starts automatically when the system boots.

- **Configuring Apache:**
  ```bash
  vi /etc/httpd/conf/httpd.conf
  ```
  The main configuration file for Apache is `httpd.conf`. Here you can set the document root, manage virtual hosts, and configure modules.

- **Restarting Apache After Configuration Changes:**
  ```bash
  systemctl restart httpd
  ```
  After making changes to the configuration, restart Apache to apply the new settings.

### **9.2 Configuring NFS**
NFS (Network File System) allows you to share directories across a network.

- **Installing NFS Utilities:**
  ```bash
  yum install nfs-utils
  ```
  The `nfs-utils` package contains the necessary tools to configure and manage NFS.

- **Configuring NFS Exports:**
  ```bash
  vi /etc/exports
  ```
  The `/etc/exports` file defines which directories are shared via NFS and which hosts can access them. Example entry:
  ```bash
  /mnt/data 192.168.1.0/24(rw,sync,no_root_squash)
  ```
  This shares the `/mnt/data` directory with the entire `192.168.1.0/24` subnet, allowing read and write access.

- **Starting and Enabling NFS Services:**
  ```bash
  systemctl start nfs-server
  systemctl enable nfs-server
  ```
  These commands start and enable the NFS server service.

- **Viewing Active NFS Exports:**
  ```bash
  exportfs -v
  ```
  This command lists the currently exported directories and their permissions.

### **9.3 Configuring Samba (SMB/CIFS)**
Samba allows file and print sharing between Linux and Windows systems.

- **Installing Samba:**
  ```bash
  yum install samba
  ```
  This installs the Samba server.

- **Configuring Samba:**
  ```bash
  vi /etc/samba/smb.conf
  ```
  The `smb.conf` file is Samba’s main configuration file. Example configuration for a shared directory:
  ```bash
  [share]
  path = /mnt/data
  valid users = @users
  guest ok = no
  writable = yes
  browsable = yes
  ```
  This shares the `/mnt/data` directory with members of the `users` group, allows them to write to it, and makes it browsable on the network.

- **Creating a Samba User:**
  ```bash
  smbpasswd -a username
  ```
  This adds a Samba user and sets a password for them.

- **Starting and Enabling Samba Services:**
  ```bash
  systemctl start smb
  systemctl enable smb
  ```
  These commands start and enable the Samba service.

---

## **10. Troubleshooting**

### **10.1 Diagnosing Network Issues**
- **Checking Network Interfaces:**
  ```bash
  ip a
  ```
  This command lists all network interfaces and their IP addresses. If an interface is down, you might need to bring it up:
  ```bash
  ip link set dev eth0 up
  ```

- **Pinging a Host:**
  ```bash
  ping 192.168.1.1
  ```
  The `ping` command tests connectivity to another network device. A successful ping shows that the network is reachable.

- **Checking Connectivity to a Specific Port:**
  ```bash
  telnet 192.168.1.1 80
  ```
  `telnet` can be used to test connectivity to a specific port on a remote server. If you can connect, the port is open and reachable.

### **10.2 System Logs**
Logs are essential for diagnosing issues.

- **Viewing General System Logs:**
  ```bash
  tail -f /var/log/messages
  ```
  `tail -f` lets you view the latest entries in the `/var/log/messages` log file and watch as new entries are added.

- **Viewing the Boot Log:**
  ```bash
  journalctl -b
  ```
  This shows all the log entries generated during the current boot session, helping you identify any startup issues.

### **10.3 Boot Issues**
If your system fails to boot, you might need to enter rescue mode.

- **Entering Rescue Mode:**
  - Boot from installation media, then select "Troubleshooting" > "Rescue a Red Hat Enterprise Linux system". This mode allows you to access your system’s files and make repairs.

- **Mounting the Root Filesystem:**
  ```bash
  chroot /mnt/sysimage
  ```
  `chroot` changes the root directory to the mounted filesystem, allowing you to interact with your system as if it were fully booted.

- **Reinstalling the GRUB Bootloader:**
  ```bash
  grub2-install /dev/sda
  grub2-mkconfig -o /boot/grub2/grub.cfg
  ```
  These commands reinstall the GRUB bootloader on the `/dev/sda` disk and regenerate the GRUB configuration file.

---

## **11. Backup and Recovery**

### **11.1 Backup with `tar`**
`tar` is commonly used for creating backups.

- **Creating a Tarball of `/etc`:**
  ```bash
  tar -cvzf /mnt/backup/etc_backup.tar.gz /etc
  ```
  This creates a compressed archive (`tarball`) of the `/etc` directory and stores it in `/mnt/backup/etc_backup.tar.gz`. The options:
  - `-c

`: Create a new archive.
  - `-v`: Verbose mode, showing the progress.
  - `-z`: Compress the archive with gzip.
  - `-f`: Specifies the filename.

- **Backing Up a Directory:**
  ```bash
  tar -cvf /mnt/backup/home_backup.tar /home
  ```
  This creates an uncompressed tarball of the `/home` directory.

### **11.2 Restore from Backup**
- **Extracting a Tarball:**
  ```bash
  tar -xvzf /mnt/backup/etc_backup.tar.gz -C /
  ```
  This extracts the `/mnt/backup/etc_backup.tar.gz` tarball into the root directory (`/`). The `-C` option specifies the directory to extract into.

- **Listing the Contents of a Tarball:**
  ```bash
  tar -tvf /mnt/backup/etc_backup.tar.gz
  ```
  This lists the files and directories contained in the tarball without extracting them.

---

## **12. Virtualization**

### **12.1 Managing KVM Virtual Machines**
KVM (Kernel-based Virtual Machine) is a virtualization solution for Linux.

- **Listing All Virtual Machines:**
  ```bash
  virsh list --all
  ```
  `virsh` is the command-line tool for managing VMs. The `--all` option lists both running and stopped VMs.

- **Starting a Virtual Machine:**
  ```bash
  virsh start myvm
  ```
  This starts the VM named `myvm`.

- **Shutting Down a Virtual Machine:**
  ```bash
  virsh shutdown myvm
  ```
  This gracefully shuts down the VM.

- **Creating a Snapshot of a VM:**
  ```bash
  virsh snapshot-create-as --domain myvm snapshot_name "Snapshot description"
  ```
  This creates a snapshot of the `myvm` VM, which you can later restore if needed.

### **12.2 Installing a Virtual Machine**
- **Creating a New Virtual Machine with `virt-install`:**
  ```bash
  virt-install --name myvm --ram 1024 --disk path=/var/lib/libvirt/images/myvm.img,size=10 --vcpus 1 --os-type linux --os-variant rhel7 --network bridge=virbr0 --graphics none --console pty,target_type=serial --location 'http://example.com/rhel7' --extra-args 'console=ttyS0,115200n8 serial'
  ```
  This command creates and starts a new VM with 1GB of RAM, a 10GB disk, 1 virtual CPU, and installs RHEL7 from a network location.

### **12.3 Managing Virtual Disks**
- **Adding a New Disk to an Existing VM:**
  ```bash
  virsh attach-disk myvm /path/to/disk.img vdb --persistent
  ```
  This attaches a new virtual disk (`/path/to/disk.img`) to the VM `myvm` as device `vdb`. The `--persistent` flag ensures the disk is attached permanently.

---

## **13. Containers**

### **13.1 Introduction to Podman**
Podman is a container management tool that allows you to manage containers without requiring a daemon like Docker.

- **Listing All Containers:**
  ```bash
  podman ps -a
  ```
  This lists all containers, including running and stopped ones.

- **Running a Container:**
  ```bash
  podman run -d -p 80:80 nginx
  ```
  This runs an NGINX container in detached mode (`-d`), mapping port 80 on the host to port 80 in the container.

- **Stopping a Container:**
  ```bash
  podman stop <container_id>
  ```
  This stops a running container. Replace `<container_id>` with the actual container ID.

- **Removing a Container:**
  ```bash
  podman rm <container_id>
  ```
  This removes a stopped container.

### **13.2 Managing Images**
- **Listing All Images:**
  ```bash
  podman images
  ```
  This lists all container images stored on the local system.

- **Pulling an Image from a Repository:**
  ```bash
  podman pull centos
  ```
  This downloads the CentOS image from a container repository like Docker Hub.

- **Removing an Image:**
  ```bash
  podman rmi centos
  ```
  This removes the CentOS image from the local system.
