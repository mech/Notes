# Linux

## udev, /dev, Device nodes/files



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

## Networking

`ifconfig` is deprecated. `ip` is the newer command.

Address Resolution Protocol (ARP) maps layer 3 IP addresses to layer 2 MAC addresses. Used when the sending IP address and the receiving IP address are on the same network.

```
// Change IP address, but not persisted!
▶ sudo ifconfig eth0 192.168.0.201 net mask 255.255.255.0 broadcast 192.168.0.255
▶ sudo ifconfig eth0 down
▶ sudo ifconfig eth0 up
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
```

### Ports

```
// See who is using port=5000
▶ netstat -tupln | grep 5000

// Find out how many ports you have open
▶ nmap <hostname>
```

## Monitoring

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

// List open files
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

