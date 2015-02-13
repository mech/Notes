# Vagrant

* [Vagrant `default` name](http://stackoverflow.com/questions/17845637/vagrant-default-name)
* [Configuration](http://docs.vagrantup.com/v2/virtualbox/configuration.html)

## CentOS 7 Box

* [Create a CentOS 6 box](http://thornelabs.net/2013/10/15/create-a-centos-6-vagrant-base-box-from-scratch-using-vmware-fusion.html)
* [Install VMware Tools](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1018414)
* [How to install VMware Tools on RHEL7](http://www.ehowstuff.com/how-to-install-vmware-tools-on-rhel-7centos-7/)
* [Installing VMware tools in a Linux VM](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1018414)

---
1. Turn Shared Folder off
2. 2 processors, 1GB RAM, Enable Hypervisor applications
3. Share with my Mac
4. HDD = 40GB, turn off Split into multiple files
5. IDE for CD/DVD bus type
6. Remove USB Controller, Remove Printer Port, Remove Sound Card
7. Uncheck Enable Drag and Drop and Enable Copy and Paste
8. Compatibility = Uncheck Allow upgrading the virtual hardware

See your kernel-devel:

`uname -a ; rpm -qa kernel\* | sort`

```
▶ yum update
▶ reboot
▶ yum install "kernel-devel-uname-r == $(uname -r)"

▶ yum provides ifconfig
▶ yum install -y net-tools wget gcc

// Check that sshd is enabled
▶ systemctl is-enabled sshd

▶ useradd vagrant
▶ mkdir -m 0700 -p /home/vagrant/.ssh
▶ wget --no-check-certificate 'https://raw.githubusercontent.com/mitchellh/vagrant/master/keys/vagrant.pub' -O /home/vagrant/.ssh/authorized_keys
▶ chmod 600 /home/vagrant/.ssh/authorized_keys
▶ chown -R vagrant:vagrant /home/vagrant/.ssh

▶ sed -i 's/^\(Defaults.*requiretty\)/#\1/' /etc/sudoers
▶ echo "vagrant ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

// Install VMware tool here

▶ yum clean all
▶ rm -rf /tmp/*
▶ rm -f /var/log/wtmp /var/log/btmp
▶ history -c
▶ shutdown -h now
```

### Create the box

```
// 1. First defragment and shrink your VMDK

▶ cd ~/Documents/Virtual\ Machines.localized/YOUR_VMWAREVM
▶ /Applications/VMware\ Fusion.app/Contents/Library/vmware-vdiskmanager -d Virtual\ Disk.vmdk
▶ /Applications/VMware\ Fusion.app/Contents/Library/vmware-vdiskmanager -k Virtual\ Disk.vmdk

// 2. Make a metadata.json

{
  "provider": "vmware_fusion"}

// 3. Remove log files

▶ rm -f vmware*.log

// 4. TAR it

▶ tar cvzf centos7.vmware.box ./*
▶ rm -f metadata.json

// 5. Move the TAR box to ~/Desktop

▶ mv centos7.vmware.box ~/Desktop
▶ vagrant box add centos7 ~/Desktop/centos7.vmware.box

// 6. Keep or remove it
▶ rm -f ~/Desktop/centos7.vmware.box
```

## Ubuntu Box

* [Create a Ubuntu 12.04 box](http://thornelabs.net/2013/09/12/create-a-ubuntu-server-1204-lts-vagrant-base-box-from-scratch-using-vmware-fusion.html)
* [Docker-friendly Vagrant base boxes by Phusion](https://github.com/phusion/open-vagrant-boxes)

```
▶ sudo -s
▶ apt-get update
▶ apt-get upgrade -y
▶ apt-get dist-upgrade -y
▶ reboot

▶ sudo apt-get install linux-headers-$(uname -r) build-essential

▶ sudo bash -c 'echo "vagrant ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers'
▶ mkdir -m 0700 -p /home/vagrant/.ssh
▶ wget --no-check-certificate 'https://raw.githubusercontent.com/mitchellh/vagrant/master/keys/vagrant.pub' -O /home/vagrant/.ssh/authorized_keys

// There is no need to do chmod and chown as you are vagrant user when you are doing these thing already.

// Install VMware Tool here

▶ sudo mkdir /mnt/cdrom
▶ sudo mount /dev/cdrom /mnt/cdrom
▶ cp /mnt/cdrom/VMwareTools-9.9.0-2304977.tar.gz /tmp/
▶ cd /tmp
▶ tar -zxvf VMwareTools-9.9.0-2304977.tar.gz
▶ cd /tmp/vmware-tools-distrib
▶ sudo ./vmware-install.pl
▶ umount /mnt/cdrom

// Final cleanup

▶ rm /etc/udev/rules.d/70-persistent-net.rules
▶ mkdir /etc/udev/rules.d/70-persistent-net.rules
▶ rm -rf /dev/.udev/
▶ rm /lib/udev/rules.d/75-persistent-net-generator.rules

▶ sudo apt-get clean
▶ sudo rm -rf /tmp/*
▶ sudo rm -f /var/log/wtmp /var/log/btmp
▶ history -c
▶ sudo history -c
▶ sudo shutdown -h now
```
