# Logging

* [**The Log: What every software engineer should know about real-time data's unifying abstraction**](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying)
* [Log Injection](https://www.owasp.org/index.php/Log_injection)
* [From Rails to Syslog](https://blog.flameeyes.eu/2012/01/from-rails-to-syslog-or-how-i-learned-to-stop-worrying-and-ditch-production-log#gsc.tab=0)
* [fluentd vs logstash](http://jasonwilder.com/blog/2013/11/19/fluentd-vs-logstash/)
* [Comparing monitoring options for Docker deployments](http://rancher.com/comparing-monitoring-options-for-docker-deployments/)
* [Container monitoring with Sysdig Cloud](https://sysdig.com/distributed-container-monitoring-sysdig-cloud-revolution/)
* [Comprehensive monitoring for Docker](https://www.sumologic.com/2015/06/16/comprehensive-monitoring-for-docker-more-than-just-logs/)
* [Log Docker events with a Ruby gem](http://blog.scoutapp.com/articles/2015/06/05/monitoring-docker-events)
* [Docker 1.8 with fluentd as logging driver](http://blog.treasuredata.com/blog/2015/08/03/5-use-cases-docker-fluentd/)
* [Making logs awesome](http://jamesthom.as/blog/2015/07/08/making-logs-awesome-with-elasticsearch-and-docker/)

Options:

* [Spotify's syslog-redirector](https://github.com/spotify/syslog-redirector)
* [supervisor-remote-logging](https://github.com/newrelic/supervisor-remote-logging)
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
* [Logsene](http://sematext.com/logsene/index.html)

Stream all your Docker logs to a centralized logging service. Never write to a log file always to stdout. If you have to write to a log file, you're violating several rules and will have to script around it so that long running containers do not run out of disk space. Treat logs as event stream.

**Data acquisition and forwarding to a centralized log store**

## ELK Stack

* [Docker 1.6 and centralized logging](http://technologyconversations.com/2015/05/18/centralized-system-and-docker-logging-with-elk-stack/)

## Syslog

**Mac OS-X: syslogd and aslmanager**

```
▶ cat /etc/syslog.conf
▶ cat /etc/asl.conf

# Rules for /var/log/system.log
> system.log mode=0640 format=bsd rotate=seq compress file_max=5M all_max=50M
```

* [**Syslog logging driver for Docker**](http://www.wolfe.id.au/2015/05/03/syslog-logging-driver-for-docker/)

```
▶ dmesg | grep something | less
▶ tail -n 10 -f /var/log/syslog
```

## Docker Logging Solution

If you're running a process on a box, you might expect the output to go to a local log file, or you might expect the output to simply be logged to the kernel buffer where it can be read from `dmesg`. Because of container's restrictions, neither of these will work without some gyrations to do so.

By default, log is sent to `stdout` or `stderr` in the container by Docker daemon and stream into a configurable backend. This backend resides at `/var/lib/docker/containers/:container_id`

```
▶ docker logs -f container_id

// Turn off logging by
--log-driver=none
```

While Docker automatically captures logs for you, it does not also rotate them. YOU NEED TO FIND YOUR LOG STREAMING SOLUTION!

Best practice is to send your container logs to syslog with `--log-driver=syslog`. Docker will now write to `/dev/log` which will be read by the syslog daemon. You also cannot use `docker logs` anymore as there is no more JSON log file to view.

```
▶ docker run -d -p 80:80 --log-driver=syslog nginx:latest
```

* [How to centralise your Docker logs with Fluentd and ElasticSearch on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-centralize-your-docker-logs-with-fluentd-and-elasticsearch-on-ubuntu-14-04)
* [Collection Docker container stdout/stderr logs](http://www.fluentd.org/guides/recipes/docker-logging)
* [Collecting Docker log files with Fluentd - Kubernetes](https://github.com/GoogleCloudPlatform/kubernetes/tree/master/cluster/addons/fluentd-elasticsearch/fluentd-es-image)

## Logstash

* [How to pack Logstash forwarder in Docker containers](http://boynux.com/logstash-forwarder-docker/)
* [Part 2](http://boynux.com/logstash-forwader-docker-part-2/)

## Logrotate

* [Understanding logrotate utility](http://www.rackspace.com/knowledge_center/article/understanding-logrotate-utility)
* [How to manage log files with logrotate](https://www.digitalocean.com/community/tutorials/how-to-manage-log-files-with-logrotate-on-ubuntu-12-10)
* [How to rotate logs to S3](http://www.dowdandassociates.com/blog/content/howto-rotate-logs-to-s3/)
* [Copy your server logs to S3](http://www.shanestillwell.com/2013/04/04/copy-your-server-logs-to-amazon-s3-using-logrotate-and-s3cmd/)
* [Logrotate with 10 examples](http://www.thegeekstuff.com/2010/07/logrotate-examples/)
* [Rotating log](http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/)

## Sending log to email using command line

* [ssmtp and mpack](http://ozzmaker.com/2012/12/03/send-email-from-the-raspberry-pi-or-linux-command-line-with-attachments/)

# Monitoring

```
▶ docker stats container_id

// To see process tree and docker-proxy
▶ ps axlfww
▶ ps -ejH
▶ pstree `pidof docker`
▶ pstree -p `pidof docker`
```

* [**cAdvisor - Google graphs for understanding resource usage**](https://github.com/google/cadvisor)
* [How to setup Docker monitoring](https://www.brianchristner.io/how-to-setup-docker-monitoring/)
* [Docker-mon - Console monitoring](https://github.com/icecrime/docker-mon)