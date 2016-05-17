# Ubuntu

* [Basic setup for a new Linux server](http://devo.ps/blog/basic-setup-for-a-new-linux-server/)
* [Bootable USB](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
* [Lightweight server GUI](http://www.htpcbeginner.com/lightweight-desktop-environment-for-ubuntu-server/)
* [Hardening 14.04](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)
* [Disable IPv6](http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04)
* [How to add and delete users on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-an-ubuntu-14-04-vps)
* [Enter SSH passphrase once](http://askubuntu.com/questions/362280/enter-ssh-passphrase-once)

## Supermicro

Press `<Ctrl>+R` to enter MegaRAID BIOS.

Press `<Del>` to enter AMI BIOS setup.

Drive Group 0 has 2 Virtual Drives in RAID Level 1.

* Restore on AC Power Loss
* 

## Brand New

```
▶ sudo bash -c 'echo "deploy ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers'
```

## Firewall UFW

* [Digital Ocean tutorial on UFW](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

```
// Before enabling UFW, allow SSH first
▶ sudo ufw allow ssh_port/tcp

▶ sudo ufw enable
▶ sudo ufw status verbose
▶ sudo ufw show added

// For 14.04
▶ sudo grep '^### tuple' /lib/ufw/user*.rules

// For 16.04
// User defined rules are stored in /etc/ufw/user.rules
▶ sudo grep '^### tuple' /etc/ufw/user*.rules
```

## Hardening Ubuntu

* [**Harden Ubuntu**](http://hardenubuntu.com/)
* [Hardening the security of Ubuntu 14.04](https://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)
* []()

```
▶ grep processor /proc/cpuinfo | wc -l
▶ sudo apt-get install htop dstat
▶ sudo dmidecode --type memory
▶ dstat --top-io --top-bio

▶ sudo bash -c 'echo "deploy ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers'

// Choose startup services like ntsysv
▶ apt-get install sysv-rc-conf

// Find what filesystem you using
▶ df -h -T
▶ lsblk -f
```

## Create Bootable USB for PC and Mac

```
▶ hdiutil convert -format UDRW -o ~/Desktop/Ubuntu/ubuntu-14.04.3-server-amd64 ubuntu-14.04.3-server-amd64.iso

// Identify your USB device, take note of /dev/diskN where N is the number
▶ diskutil list

▶ diskutil unmountDisk /dev/diskN

▶ sudo dd if=/Users/mech/Desktop/Ubuntu/ubuntu-14.04.3-server-amd64.dmg of=/dev/rdiskN bs=1m

// Mac OS-X will display a prompt to ask you to reject, if not do the following
▶ diskutil eject /dev/diskN
```

## Install GUI on Server

```
▶ 
```

## Disable IPv6

```
▶ sudo vi /etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

// Reload configuration
▶ sudo sysctl -p

// Should see "1"
▶ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

## Landscape and MOTD

Remove the annoying landscape motd:

```
▶ sudo vi /etc/landscape/client.conf

[sysinfo]
exclude_sysinfo_plugins = LandscapeLink

▶ sudo chown landscape:landscape /etc/landscape/client.conf
```

Go to `/etc/update-motd.d`



## SSH

* [Protect multiple authentication errors using fail2ban](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04)

```
// 1st: backup your existing config
▶ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults
▶ sudo chmod a-w /etc/ssh/sshd_config.factory-defaults
```

To see failed password attempts:

```
▶ cat /var/log/auth.log | grep "Failed password"
Mar 24 15:01:42 bastion sshd[2768]: Failed password for deploy from 192.168.1.10 port 49641 ssh2
```

Edit your `/etc/ssh/sshd_config`:

```
PasswordAuthentication no
PermitRootLogin no
LogLevel VERBOSE
Port ??
```

Then restart by `sudo service ssh restart`

**Enter passphrase once so that git pull won't repeatedly ask for passphrase**

```
▶ ssh-agent bash
▶ ssh-add /home/username/.ssh/id_rsa
```

## sysctl.conf

Kernel flags set with `sysctl` tool will be lost upon reboot. In order to persist them, you must add them to `/etc/sysctl.conf` or `/etc/sysctl.d/`.

Typical thing to tweak here is increase open files limit, increase queue for listening on new connection like `net.core.somaxconn`.

* [Linux tuning](https://rtcamp.com/tutorials/linux/sysctl-conf/)

```
▶ sysctl -A
▶ sysctl net.core.somaxconn
```

## Harden Network

Edit `/etc/sysctl.d/10-network-security.conf`

```
# Ignore ICMP broadcast requests
net.ipv4.icmp_echo_ignore_broadcasts = 1

# Ignore Directed pings
net.ipv4.icmp_echo_ignore_all = 1

# Ignore ICMP redirects
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv6.conf.default.accept_redirects = 0

# Block SYN attacks
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 5

# Log Martians
net.ipv4.conf.all.log_martians = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1

# Ignore send redirects
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0

# Disable source packet routing
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0 
net.ipv4.conf.default.accept_source_route = 0
net.ipv6.conf.default.accept_source_route = 0
```

Restart using `sudo service procps start`

## Releases

64-bit is called `amd64` and 32-bit is called `i386`. It is called `amd64` because AMD developed the 64-bit instruction extensions. Athlon 64 was the first to release 64-bit x86(x86-64) CPUs.

* 16.04 - Xenial Xerus (4.4.0-21)
* 14.04.3 - 3.19.0-26
* 14.10 - Utopic (3.16.0-23-generic)
* 14.04.2 - (3.16.0-30-generic)
* 14.04 - Trusty
* 13.10 - Saucy
* 13.04 - Raring
* 12.10 - Quantal
* 12.04 - Precise
* 10.04 - Lucid

```
▶ lsb_release -r -c -d

// Check how many packages you have
▶ dpkg -l | wc -l

// Find which package installed the binary/file
▶ dpkg -S vmstat

// List files installed by a package
▶ dpkg -L ufw
```

## Update and Upgrade

```
▶ apt-get clean
▶ apt-get update
▶ apt-get upgrade
▶ apt-get dist-upgrade

▶ shutdown -r now

// To see what updates are available
▶ /usr/lib/update-notifier/apt-check -p
```

## Locale

```
▶ locale-gen en_US.UTF-8 && echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale

// To test it
▶ locale
```

## IP Addresses

* [Assign multiple IP addresses to one interface](http://askubuntu.com/questions/547289/how-can-i-from-cli-assign-multiple-ip-addresses-to-one-interface)
* [Subnet Calculator](http://www.subnet-calculator.com/)
* [IP command examples](http://www.tecmint.com/ip-command-examples/)

```
// Will be lost after reboot
▶ sudo ip address add 172.16.100.17/24 dev eth0
▶ ip address show eth0
▶ sudo ip address del 172.16.100.17/24 dev eth0

// To make it permanent, edit
▶ vi /etc/network/interfaces

iface eth0 inet dhcp

iface eth0 inet static
  address 172.16.100.17/24

iface eth0 inet static
  address 172.16.24.11/24
  
iface eth0 inet static 
  address 10.1.2.3 
  netmask 255.255.240.0 
  broadcast 10.1.255.255
  dns-nameservers 10.1.2.3 10.1.2.3
  dns-search example.com
  gateway ...
  
// Activate these settings without reboot
// Must be in one line or else your SSH session will not survive
▶ sudo ifdown eth0 && sudo ifup eth0
```

## APT

Differences between `sudo apt-get install htop` and `sudo apt install htop`?

```
▶ apt search ??
▶ aptitude search "?name(^bind)"
```

When you run `apt-get update`, a list of packages will get downloaded and these files are then stored in `/var/lib/apt/lists/`. You can safely remove the contents of that directory as it is recreated when you refresh the package lists.

### PPA - Personal Package Archives

* [Brightbox Ruby packages](https://www.brightbox.com/docs/ruby/ubuntu/)

May need `software-properties-common`

```
▶ sudo add-apt-repository ppa:git-core/ppa
▶ sudo apt-get update
▶ sudo apt-get install git
```

## How do you upgrade kernel?

```
▶ lsb_release -a
▶ uname -r
3.16.0-23-generic

▶ apt-get update
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

// We can do a dist-upgrade also

▶ apt-get upgrade
▶ apt-get dist-upgrade  

// Following may not be performed

▶ apt-cache search linux-image
▶ apt-get install linux-image-generic-lts-utopic linux-headers-generic-lts-utopic
▶ update-grub
▶ shutdown -r now
```

```
▶ sudo su
▶ sudo -s
```

## How to find and do patching?

* [CVE-2014-0224](http://www.liquidweb.com/kb/update-and-patch-openssl-on-ubuntu-for-the-ccs-injection-vulnerability/)

```
▶ apt-get changelog openssl | grep CVE-2014-0224
    - debian/patches/CVE-2014-0224-regression2.patch: accept CCS after
    - debian/patches/CVE-2014-0224.patch: set the CCS_OK flag when using
    - debian/patches/CVE-2014-0224-1.patch: only accept change cipher spec
    - debian/patches/CVE-2014-0224-2.patch: don't accept zero length master
    - debian/patches/CVE-2014-0224-3.patch: allow CCS after resumption in
    - CVE-2014-0224
```

## Installing Docker Engine

```
// Edit DOCKER_OPTS AT:
▶ vi /etc/default/docker
```

Remember to enable "Memory and Swap Accounting".

* [**The memory cgroups and swap accounting**](http://docs.docker.com/installation/ubuntulinux/#memory-and-swap-accounting). Use `GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"`.
* [UFW - Uncomplicated Firewall](https://help.ubuntu.com/community/UFW)
* [How to setup a firewall with UFW](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)
* [Upgrading Docker](http://blog.thestateofme.com/2015/06/23/upgrading-docker/)

We need to use the Docker team's DEB packages.

**New way for 16.04**

```
▶ sudo apt-get update

▶ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

▶ sudo vi /etc/apt/sources.list.d/docker.list

deb https://apt.dockerproject.org/repo ubuntu-xenial main

▶ sudo apt-get purge lxc-docker
▶ apt-cache policy docker-engine
▶ sudo apt-get install linux-image-extra-$(uname -r)
▶ sudo apt-get install docker-engine
▶ sudo service docker start

▶ sudo groupadd docker
▶ sudo usermod -aG docker deploy
▶ // log out and in again

// Adjust memory and swap accounting
▶ sudo vi /etc/default/grub

GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"

▶ sudo update-grub
▶ sudo shutdown -r now

// Enable UFW forwarding
▶ 
▶ 
```


**Old way**

```
▶ apt-get update

// Most easy way, install + upgrade
▶ curl -sSL https://get.docker.com/ | sh

// lxc-docker - Old way
▶ curl -s https://get.docker.com/gpg | sudo apt-key add -
▶ sudo sh -c "echo deb https://get.docker.com/ubuntu docker main > /etc/apt/sources.list.d/docker.list"
▶ sudo apt-get update
▶ sudo apt-get install -y -q lxc-docker

// Edit UFW

▶ vim /etc/default/ufw
DEFAULT_FORWARD_POLICY="ACCEPT"
▶ sudo ufw reload

// Upgrading is easy
▶ apt-get update
▶ apt-get install lxc-docker

// Give your user non-root docker access
▶ sudo groupadd docker
▶ sudo gpasswd -a ${USER} docker
▶ sudo service docker restart
▶ exit // Need to logout
```

```
▶ sudo usermod -aG docker deploy
```
