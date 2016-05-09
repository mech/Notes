# Linux

* [**Build this lab?**](http://www.greenhills.co.uk/2015/05/22/projectcalico-experiments.html)
* [**Basics of Unix Philosophy**](http://www.faqs.org/docs/artu/ch01s06.html)
* [First 5 minutes troubleshooting a server](http://devo.ps/blog/troubleshooting-5minutes-on-a-yet-unknown-box/)
* [Linux TCP/IP tuning for scalability](http://www.lognormal.com/blog/2012/09/27/linux-tcpip-tuning/)
* [Allow setting `ulimits` for containers](https://github.com/docker/docker/pull/9437)
* [Understanding Linux CPU stats](http://blog.scoutapp.com/articles/2015/02/24/understanding-linuxs-cpu-stats)
* [**Lynis - Security auditing**](https://cisofy.com/lynis/)
* lynis, rkhunterm chkrootkit, tripwire, tiger, bastille, unhide, unhide.rb, aide, bsign, systraq, snort, psad, samhain
* [sysdig](http://www.sysdig.org/)

```
// 6 minutes to shutdown with this file /etc/nologin
▶ sudo shutdown -h +6 "System going down, please logout!" 
```

```
▶ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic root=UUID=f9868a3d-1a9c-4161-9f88-326eecf54f25 ro
```

## Cron

* [Schedule Tasks on Linux Using Crontab](http://kvz.io/blog/2007/07/29/schedule-tasks-on-linux-using-crontab/)

---

- minute (from 0 to 59)
- hour (from 0 to 23)
- day of month (from 1 to 31)
- month (from 1 to 12)
- day of week (from 0 to 6) (0=Sunday)

## Init

* Systemd
* Upstart
* init.d



## UID, GID, and Permission

```
▶ id -u vagrant # 1000
▶ id -g vagrant # 1000
▶ id -G vagrant
▶ id vagrant
```

## udev, /dev, Device nodes/files

* [Cron script for checking disk space](http://blog.rimuhosting.com/2012/02/20/cron-script-for-checking-disk-space/)

```
▶ mount
▶ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
▶ lspci | grep RAID
```

## Runlevels

```
/sbin/init
/etc/inittab
/etc/init.d/rc
/etc/rc.d/rc
```

```
▶ who -r

id:5:initdefault:
```

## Compile and build C program

```
▶ sudo yum groupinstall "Development Tools"
▶ sudo apt-get install build-essential

▶ ./configure --with-A --without-B
▶ make
▶ sudo make install
```

## Logs

`dmesg` prints the contents of the "Kernel Ring Buffer". This information is also send in real-time to `syslogd` and ends up in `/var/log/messages`. Where `dmesg` is most useful is in capturing boot-time messages before `syslogd` started.

```
// Display message or driver message, thus the "D" in dmesg
// Show Kernel ring buffers
▶ dmesg
▶ dmesg | grep -i eth0
▶ dmesg | grep something | less

▶ tail -n 10 -f /var/log/syslog
▶ less /var/log/messages
▶ less /var/log/secure
▶ less /var/log/auth
```

There are several things logged into `/var/log/messages` including mail, cron, daemon, kern, auth, etc.


## Networking

* [The Internet Super Server inetd](https://www.netbsd.org/docs/guide/en/chap-inetd.html)

`ifconfig` is deprecated. `ip` is the newer command.

3 things you need to check:

1. Your IP address: `ip a s`
2. Your subnet mask: `nmap --iflist`
3. Your default gateway `0.0.0.0`

Address Resolution Protocol (ARP) maps layer 3 IP addresses to layer 2 MAC addresses. Used when the sending IP address and the receiving IP address are on the same network.

```
// Find public IP address - http://askubuntu.com/questions/95910/command-for-determining-my-public-ip
▶ curl -s checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
▶ curl ifconfig.me
▶ curl ifconfig.me/host

// Change IP address, but not persisted!
▶ sudo ifconfig eth0 192.168.0.201 net mask 255.255.255.0 broadcast 192.168.0.255
▶ sudo ifconfig eth0 down
▶ sudo ifconfig eth0 up

▶ sudo ifdown eth0
▶ sudo ifup eth0
```

```
▶ ip address show
▶ ip a s
▶ ip -4 a s        // Show IPv4
▶ ip route show
▶ ip rs
▶ ip neighbor show
▶ ip n s

// Add IP address
▶ sudo ip a a 192.168.1.199/24 dev eth0

// Delete IP address
▶ sudo ip a d 192.168.1.199/24 dev eth0

// Capture 5 packets, but not port 22 on interface eth0
▶ sudo tcpdump -c 5 -i eth0 not port 22

▶ ldd /usr/sbin/sshd | grep wrap
```

### Ports

```
// See who is using port=5000
▶ netstat -tupln | grep 5000

// See if MySQL is listening to correct port
▶ sudo netstat -tap | grep mysql

// Find out how many ports you have open
▶ nmap <hostname>
▶ nmap -v -sT localhost      // Scan for open ports
▶ sudo nmap -v -sS localhost // SYN scanning
▶ sudo nmap <hostname>       // More information like MAC address
▶ nmap --iflist
▶ nmap -p80 <hostname>
▶ sudo nmap -sV <hostname> // Find software version
▶ sudo nmap -A <hostname>  // Find OS
▶ sudo nmap -p80 --script http-enum <hostname>
▶ sudo nmap -p80 --script http-enum --script-args http-enum.displayall <hostname>
```

## Monitoring

* [80 Linux Monitoring Tools](https://blog.serverdensity.com/80-linux-monitoring-tools-know/)

Real-time (vmstat, ps, uptime, w, lsof, netstat) vs Historical (sysstat)

```
// r - Total number of processes waiting for CPU time
// b - Total number of blocked processes, waiting for disk or network IO
// swpd - Used virtual memory
// free - Free virtual memory
// buff - Memory used as buffers (what's in directories, permissions)
// cache - Memory used as cache (contents of files)
// si - Memory swapped from disk every second
// so - Memory swapped to disk every second
// bi - Blocks in per second
// bo - Blocks out per second
// in - Interrupts per second
// cs - Context switches per second
▶ vmstat
▶ vmstat -S M     // Change to MB
▶ free -m         // Show active/inactive memory
▶ vmstat 5 3      // 5 seconds and run it 3 time
▶ watch -d vmstat // See the changes in real-time

// 1min, 5min, 15min
▶ uptime
 15:31:27 up 22 min,  1 user,  load average: 0.00, 0.02, 0.03

// l - Listening
// t - TCP
// u - UDP
// x - Unix socket
▶ netstat -altux
▶ netstat -i
▶ netstat -s
▶ netstat -nr   // Display route table, same as route
▶ netstat -ntlp // Who is listening on TCP 
▶ netstat -nulp // Who is listening on UDP
▶ netstat -nxlp // Who is listening on socket
▶ ss -s         // netstat can be slow to display all connections

// List open files
▶ sudo lsof -i
▶ sudo lsof -iTCP:22

// 
▶ sudo iptables -nvL
▶ watch -d sudo iptables -nvL

// 
▶ ps -elf
▶ pstree
```

```
▶ sudo apt-get install sysstat
▶ sar -V
▶ sar -w -f /var/log/sa/sa11
```

### collectd

```
▶ yum repolist
▶ yum install -y collectd collectd-rrdtool rrdtool collectd-web httpd

▶ vi /etc/collectd.conf

```

### Nagios

## Backup

Compressing (tar.gz) and uploading to Amazon S3

```
// c - create
// v - verbose
// z - zip
// f - file
▶ tar -cvf etc.tar /etc
▶ gzip etc.tar

▶ tar -czf etc.tar.gz /etc
▶ tar -tzf etc.tar.gz
▶ tar -xzf etc.tar.gz
```
