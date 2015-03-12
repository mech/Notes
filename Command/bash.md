# Bash

* [Differences between login and non-login shell](http://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell/46856#46856)
* [Cron email only errors](http://serverfault.com/questions/226074/cron-only-get-errors-in-emails)
* [Chmod Calculator](http://chmodcalc.com/)
* [10 tips for wonderful bash productivity](https://developer.atlassian.com/blog/2015/02/ten-tips-for-wonderful-bash-productivity/)

```
shutdown now    # Shutdown
shutdown -h now # Halt
shutdown -r now # Reboot
logout          # Logout to refresh session terminal?
cd -            # Go back to previous directory
sudo su -       # Login as root
logout          # Logout from root
ls; cd /tmp     # Separate command with ;
vim &           # Put it in the background
fg              # Bring the previous vim to the foreground
file next.png   # Show details of the file
printenv        # Print environment variables
ls -l           # List file permission
ls -l /boot/*$(uname -r)* # You can execute system command also
!$              # Access to the last file
!!              # Re-run the last command
ps auxw | egrep '\[' # Kernel processes
sudo lsmod      # See what modules the kernel loaded
history -c      # Clear your command history
top -o cpu      # Order top to CPU
id              # Print user ID
tree -L 1 /     # Print first level tree
sudo fdisk -l   # Show disks
chmod u+rwx,g-rwx,o-rwx file # Give User Read/Write/Execute
ls -dl          # List directory
getfacl file    # More detailed file permission
man -k time
man 3 printf
echo $PATH | tr ':' '\n' # tr is translate characters
ls > file_list.txt   # Save to a file first, then sort it
sort < file_list.txt # File feed into sort command
cp /etc/hosts . # Copy to the current directory
cut -f 1 -d : /etc/passwd # Use : as the delimiter
du -hs # Disk usage in human summary
set -o history   # Enable command history
unset -o history # Disable command history
history -c       # Clear history
tree folder -d
pwd -P # true full path
grep root /etc/* # Check every files that contain the word root
df -h # Disk usage
< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c12 | xargs echo
grep -v // !$ | grep -v ^$ # Clean out comment
sed -i -e 's/127.0.0.1/0.0.0.0/' /etc/mysql/my.cnf
```

`/proc/sys/net/ipv4` is where you configure your TCP/IP.

`.bashrc` will be run whenever you run an interactive shell. If you type `bash` 5 times to enter an inception, then you need to type `exit` 5 times as well.

`.bash_profile` is for personal settings and variables that get execute whenever you use a remote login like SSH.

## .dot

* [mrmartineau](https://github.com/mrmartineau/dotfiles)

## find

`find` can take a long time. `locate` is another alternative. It is quicker.

```
find / # Find files at the root directory
find / -name "*.rpm" 2> /dev/tty6 # stderr to another terminal and inspect later

find / -name "*.rpm" >> rpm-result.txt 2> /dev/null # Append to rpm and send error to black hole

find / -user mech # Find user mech

find / -perm /4000 # Find file with such permission

which passwd   # Only for binary
whereis passwd # More broadly, can find man pages, etc.

locate passwd # Fast by not real-time. Need updatedb
```


## Process

```
pgrep -lf syslog              # See PID
ps auxw | egrep -v \] | less  # Not showing kernel process
ping google.com > /dev/null & # Put into the background
```

## sudo

"Superuser" Do

```
sudo visudo # Edit the sudoer list
```

Find the ticket for 5 minutes at `/var/db/sudo`

## OpenSSL

To know if you are effected or not:

```
rpm -q --changelog openssl | less
rpm -q --changelog openssl | grep CVE-2014-0224
```

```
yum info openssl
yum update openssl
```

## TCP/IP

* TCP Fast Open
* Buffer bloat

```
sudo dmesg | less
sudo lspci | less
sudo ethtool eth0

ip addr show
ip route show # Show which IP is being linked to

netstat -rn # Deprecated!

# To add more IP to the interface, but not persisted
sudo ip addr add 192.168.10.10/24 dev eth0:1

# To remove the IP
sudo ip addr del 192.168.10.10/24 dev eth0:1
```

Go to `/etc/sysconfig/network-scripts` to find `ifcfg-eth0` to persist your changes on IP.

```
DEVICE="eth0:1"
BOOTPROTO="none" # if not DHCP
ONBOOT="yes"
IPADDR=58.xx.xx.xx
```

Then bring the interface up using `sudo ifup eth0:1`

```
netstat -tnl
less /etc/services
sudo netstat -anlp
sudo fuser 22/tcp # To see which application is using which port
sudo ss -a # To see all connection
grep ssh /etc/services # Find port for SSH
```

`/proc/sys/net/ipv4`

IP CIDR Notation - See http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing

```
dig +short google.com # nslookup is deprecated, use dig
dig google.com mx
dig yeoman.io | grep -E '(207.97.227.245|204.232.175.78|199.27.73.133)'
```

## ping, traceroute, tracepath, netcat, tcpdump, wireshark



## Access Control

Objects (processes, files) have owners. The creator of an object owns it.

```
ls -l file
-rw-r--r--   1 mech  staff    2382 Jul  6 20:08 Gemfile
grep mech /etc/passwd
grep ^staff /etc/group #=> staff:*:20:root
```

`mech` is the creator of the object `Gemfile` and `staff` is the group

## Moving around text

* `Ctrl + A` to move to beginning of line
* `Ctrl + E` to move to end of line
* `Ctrl + U` to delete whole text and put into pasteboard
* `Ctrl + Y` to paste the previously deleted text

## Pipe and Redirection

```
ps ax > ps.txt
echo "Appending..." >> ps.txt
ps aux | grep bash

text="Test"
echo $text
ls_text=$(ls -l) # Assign the result of the ls -l to the variable ls_text
echo "$ls_text"  # variable are interpolated by the shell
echo '$ls_text'
```

## grep

```
egrep ^r /etc/passwd              # Find all that starts with 'r'
egrep '[bash|false]$' /etc/passwd # Find all that ends with bash or false

grep lisa * 2> /dev/null # If we do not want to see too many error output

grep -B 3 -A 2 foo README.txt
```

## Filtering

```
cut -f 1 -d ':' /etc/passwd # Print out only the first field with delimiter of ":"

cut -f 1 -d ':' /etc/passwd | sort | uniq | head -5 # Show first 5
cut -f 1 -d ':' /etc/passwd | sort | uniq | tail -5 # Show last 5
```

## History

```
history # Access your command history
!XXX    # See the history number and execute it quickly
```

`Ctrl + R` will become `(reverse-i-search)`. Press again to cycle through the keywords.

## Bash Script

```
#!/bin/bash

if [[ $# != 1 || $1 == "-h" ]]; then
  echo "Usage:"
  exit 1
fi

file=$1
```

## Crontab

`minute  hour  dom  month  weekday  command`

```
# 7:30am email yourself to work!
30 7 * * 1-5 echo 'Get up!' | mail -s "work day" mech@me.com

# Every 15 minutes
*/15 * * * * uptime >> ~/uptimes
```

See `/etc/cron.daily`

## Log files and Syslog (rsyslog)

```
ps auxw | grep syslog
logger -p info Hello syslog
```

`/etc/logrotate.conf`

You can configure `rsyslog` to send logs to a remote server.

## DTrace

* [Top 10 DTrace scripts](http://dtrace.org/blogs/brendan/2011/10/10/top-10-dtrace-scripts-for-mac-os-x/)


```
sudo iosnoop
```