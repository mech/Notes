# Ubuntu

* [Basic setup for a new Linux server](http://devo.ps/blog/basic-setup-for-a-new-linux-server/)
* [Bootable USB](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)

```
▶ sudo apt-get install htop dstat

▶ dstat --top-io --top-bio
```

## Releases

64-bit is called `amd64` and 32-bit is called `i386`. It is called `amd64` because AMD developed the 64-bit instruction extensions. Athlon 64 was the first to release 64-bit x86(x86-64) CPUs.

* 14.10 - Utopic (3.16.0-23-generic)
* 14.04.2 - (3.16.0-30-generic)
* 14.04 - Trusty
* 13.10 - Saucy
* 13.04 - Raring
* 12.10 - Quantal
* 12.04 - Precise
* 10.04 - Lucid

```
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
```

## Locale

```
▶ locale-gen en_US.UTF-8 && echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale

// To test it
▶ locale
```

## IP Addresses

* [Assign multiple IP addresses to one interface](http://askubuntu.com/questions/547289/how-can-i-from-cli-assign-multiple-ip-addresses-to-one-interface)

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
  
// Activate these settings without reboot
// Must be in one line or else your SSH session will not survive
▶ sudo ifdown eth0 && sudo ifup eth0
```

## APT

```
▶ apt-cache search ??
```

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

## Installing Docker

Remember to enable "Memory and Swap Accounting".

* [**The memory cgroups and swap accounting**](http://docs.docker.com/installation/ubuntulinux/#memory-and-swap-accounting)
* [UFW - Uncomplicated Firewall](https://help.ubuntu.com/community/UFW)
* [How to setup a firewall with UFW](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)

We need to use the Docker team's DEB packages.

```
▶ apt-get update

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