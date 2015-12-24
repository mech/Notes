# Security for Rails

* [Ruby on Rails Security Guide](http://guides.rubyonrails.org/security.html)
* [OWASP's cheatsheet](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)

## Basic Tools

* [URL Encode/Decode](http://www.url-encode-decode.com/)
* [Harvest emails](https://github.com/laramies/theHarvester)
* [OWASP ZAP](https://github.com/zaproxy/zaproxy)
* [Search Code](https://searchcode.com)
* [Beef: XSS](http://beefproject.com/)

```
▶ pip install requests
▶ python theHarvester.py -d {domain} -b all
```

```
// cut, sort, uniq and change everything to lowercase
▶ cat yob*.txt | cut -d , -f 1 | sort | uniq
▶ awk '{print tolower($0)}'

// Or in one line
▶ cat yob*.txt | cut -d , -f 1 | sort | uniq | awk '{print tolower($0)}' > firstnames.txt
▶ cat firstnames.txt | sed -e 's/$/@onemonthsimple.com/' > usernames-onemonthsimple.txt
```

## Gems

* [rack-attack](https://github.com/kickstarter/rack-attack)