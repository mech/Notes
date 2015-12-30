# Security for Rails

* [Ruby on Rails Security Guide](http://guides.rubyonrails.org/security.html)
* [OWASP's cheatsheet](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)
* [Sakurity Blog](http://sakurity.com/blog)
* [Mathias's Blog](https://mathiasbynens.be/)
* [OWASP Rails Cheatsheet](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)
* [OWASP Singapore Chapter](https://www.owasp.org/index.php/Singapore)
* [Open Redirect Vulnerability](http://homakov.blogspot.sg/2014/01/evolution-of-open-redirect-vulnerability.html)

## Basic Tools

* [Burp Proxy](https://portswigger.net/burp/proxy.html)
* [URL Encode/Decode](http://www.url-encode-decode.com/)
* [Harvest emails](https://github.com/laramies/theHarvester)
* [OWASP ZAP](https://github.com/zaproxy/zaproxy)
* [Search Code](https://searchcode.com)
* [Beef: XSS](http://beefproject.com/)
* Brakeman

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

## System Commands

Don't use `system()`! If you must, use `-p` to parameterise it.

## Mass Assignment and Strong Parameters

* [Github hacked!](https://github.com/blog/1068-public-key-security-vulnerability-and-mitigation)
* [How Homakov hacked GitHub and the line of code that could have prevented it](https://gist.github.com/peternixey/1978249)

## Regular Expression

Capital `A` and `Z`.

## Content Security Policy

* [CSP in GitHub](https://github.com/blog/1477-content-security-policy)
* [CSP Report](https://www.tollmanz.com/content-security-policy-report-samples/)

## Gems

* [rack-attack](https://github.com/kickstarter/rack-attack)
* [secureheaders](https://github.com/twitter/secureheaders)