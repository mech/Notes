# Security

* [Expose any folder as HTTPS fileserver](https://github.com/inconshreveable/srvdir)
* [ShellShock](http://alblue.bandlem.com/2014/09/bash-remote-vulnerability.html)

## NSA

* [How NSA plans to infect millions of computers with malware](https://firstlook.org/theintercept/article/2014/03/12/nsa-plans-infect-millions-computers-malware/)

## SSL

The CPU cost of 256-bit encryption is very low, comparable to compression algorithms. The extra ~500ms latency of the 7-way SSL handshake only occurs once per web connection.

* [Check your SSL](https://sslcheck.globalsign.com/en_US)
* [Another SSL check tool from GeoTrust to check for SHA1](https://ssltools.geotrust.com/checker/views/certCheck.jsp)
* [Heartbleed bug](http://heartbleed.com/)
* [A basic guide to when and how to deploy HTTPS](http://erik.io/blog/2013/06/08/a-basic-guide-to-when-and-how-to-deploy-https/)
* [Re-issue](https://knowledge.rapidssl.com/support/ssl-certificate-support/index?page=content&id=SO5757)
* [Replacing SHA-1 with SHA-2](https://knowledge.rapidssl.com/support/ssl-certificate-support/index?page=content&id=SO26409)

Setting the `AllowUsers` in `sshd_config`