# Logging

* [Log Injection](https://www.owasp.org/index.php/Log_injection)
* [From Rails to Syslog](https://blog.flameeyes.eu/2012/01/from-rails-to-syslog-or-how-i-learned-to-stop-worrying-and-ditch-production-log#gsc.tab=0)
* [fluentd vs logstash](http://jasonwilder.com/blog/2013/11/19/fluentd-vs-logstash/)

Options:

* [logstash](http://logstash.net/)
* [logentries](https://logentries.com/)
* [fluentd](http://www.fluentd.org/)
* [loggly](https://www.loggly.com/)
* [graylog](https://www.graylog.org/)
* statsd
* datadog

Stream all your Docker logs to a centralized logging service. Never write to a log file always to stdout. If you have to write to a log file, you're violating several rules and will have to script around it so that long running containers do not run out of disk space. Treat logs as event stream.

## Docker Logging Solution

* [How to centralise your Docker logs with Fluentd and ElasticSearch on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-centralize-your-docker-logs-with-fluentd-and-elasticsearch-on-ubuntu-14-04)
* [Collection Docker container stdout/stderr logs](http://www.fluentd.org/guides/recipes/docker-logging)
* [Collecting Docker log files with Fluentd - Kubernetes](https://github.com/GoogleCloudPlatform/kubernetes/tree/master/cluster/addons/fluentd-elasticsearch/fluentd-es-image)

## Logrotate

* [Understanding logrotate utility](http://www.rackspace.com/knowledge_center/article/understanding-logrotate-utility)