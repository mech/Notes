# Logging

* [Log Injection](https://www.owasp.org/index.php/Log_injection)
* [From Rails to Syslog](https://blog.flameeyes.eu/2012/01/from-rails-to-syslog-or-how-i-learned-to-stop-worrying-and-ditch-production-log#gsc.tab=0)
* [fluentd vs logstash](http://jasonwilder.com/blog/2013/11/19/fluentd-vs-logstash/)
* [Comparing monitoring options for Docker deployments](http://rancher.com/comparing-monitoring-options-for-docker-deployments/)
* [Container monitoring with Sysdig Cloud](https://sysdig.com/distributed-container-monitoring-sysdig-cloud-revolution/)
* [Comprehensive monitoring for Docker](https://www.sumologic.com/2015/06/16/comprehensive-monitoring-for-docker-more-than-just-logs/)
* [Log Docker events with a Ruby gem](http://blog.scoutapp.com/articles/2015/06/05/monitoring-docker-events)
* [Docker 1.8 with fluentd as logging driver](http://blog.treasuredata.com/blog/2015/08/03/5-use-cases-docker-fluentd/)

Options:

* [logstash](http://logstash.net/)
* [logspout - Log routing for Docker](https://github.com/gliderlabs/logspout)
* [logentries](https://logentries.com/)
* [fluentd](http://www.fluentd.org/)
* [loggly](https://www.loggly.com/)
* [graylog](https://www.graylog.org/)
* statsd
* datadog
* [boundary](http://www.boundary.com/)
* [Vivid Cortex](https://vividcortex.com/)

Stream all your Docker logs to a centralized logging service. Never write to a log file always to stdout. If you have to write to a log file, you're violating several rules and will have to script around it so that long running containers do not run out of disk space. Treat logs as event stream.

**Data acquisition and forwarding to a centralized log store**

## ELK Stack

* [Docker 1.6 and centralized logging](http://technologyconversations.com/2015/05/18/centralized-system-and-docker-logging-with-elk-stack/)

## Syslog

* [Syslog logging driver for Docker](http://www.wolfe.id.au/2015/05/03/syslog-logging-driver-for-docker/)

## Docker Logging Solution

* [How to centralise your Docker logs with Fluentd and ElasticSearch on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-centralize-your-docker-logs-with-fluentd-and-elasticsearch-on-ubuntu-14-04)
* [Collection Docker container stdout/stderr logs](http://www.fluentd.org/guides/recipes/docker-logging)
* [Collecting Docker log files with Fluentd - Kubernetes](https://github.com/GoogleCloudPlatform/kubernetes/tree/master/cluster/addons/fluentd-elasticsearch/fluentd-es-image)

## Logstash

* [How to pack Logstash forwarder in Docker containers](http://boynux.com/logstash-forwarder-docker/)
* [Part 2](http://boynux.com/logstash-forwader-docker-part-2/)

## Logrotate

* [Understanding logrotate utility](http://www.rackspace.com/knowledge_center/article/understanding-logrotate-utility)
* [How to manage log files with logrotate](https://www.digitalocean.com/community/tutorials/how-to-manage-log-files-with-logrotate-on-ubuntu-12-10)

# Monitoring

* [How to setup Docker monitoring](https://www.brianchristner.io/how-to-setup-docker-monitoring/)
* [Docker-mon - Console monitoring](https://github.com/icecrime/docker-mon)