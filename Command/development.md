# Development

* [Awesome Shell](https://github.com/alebcay/awesome-shell)

See surrounding lines

`cat production.log | grep S6414 -C 10`

`rails new cp -T -d postgresql -B`

`grep "alert" * -R`

`ruby -run -e httpd . -p 8080`

`python -m http.server 8080`

`curl -i -XGET 'localhost:9200/_count?pretty'`

`crontab -l > crontab.txt`
`cat crontab.txt | crontab -`

```
# The first command must succeed before the second can continue
rake test && cap deploy
```

* [Sysadmin Casts](http://sysadmincasts.com/)

"\xEF\xBF\xBD" - Or Replacement Character

`git grep ', =' | wc -l`

```
# Open Firewall port in Mavericks

sudo vim /etc/pf.conf

# Open port 8080 for TCP on all interfaces
pass in proto tcp from any to any port 8080

sudo pfctl -vnf /etc/pf.conf
```

```
# Display a list of files sorted by file size
ls -l | sort -k5n | less
```