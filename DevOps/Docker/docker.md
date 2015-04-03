# Docker

> How long would it take your organization to deploy a change that involves just one single line of code? (Lead time, cycle time) - Poppendieck (Release Cadence)

Deming Cycle - Plan, Do, Check, Act

Scientific Method - Hypothesize, Experiment, Evaluate

* [**Awesome Docker**](http://getawesomeness.com/get/docker)
* [**Valuable Docker Links**](http://www.nkode.io/2014/08/24/valuable-docker-links.html)
* [**Docker Cheat Sheet**](https://github.com/wsargent/docker-cheat-sheet)
* [**DevOps Kata**](http://devopsy.com/blog/2013/08/16/devops-kata-single-line-of-code/)
* [**Docker Forums**](https://forums.docker.com/)
* [Docker News](http://blog.getcrane.com/docker-news/the-best-of-docker-last-week-2nd-march)
* [Docker Weekly](http://blog.docker.com/docker-weekly-archives/)
* [Giant Swarm blog](http://blog.giantswarm.io/)
* [Tutum blog](http://blog.tutum.co/)
* [Game Changer blog](http://tech.gc.com/)

Docker is a workflow and tooling. Docker wants you to make lots of small changes instead of huge, big bang updates. Smaller changes mean reduced risk and more uptime.

Containers as services instead of virtual machines. Following the example of Heroku (12Factors)

Tighten iteration loop.

OODA loop - Observe, Orient, Decide, Art. The one that win is the one that can go around this loop the fastest. Move the fastest, iterate the fastest.

Developer worries about what's "inside" the container. His code, libraries, package manager, apps and data. All Linux server to them look the same.

Ops worries what's "outside" the container. Login, remote address, monitoring, network config. All containers start, stop, copy, attach, migrate the same way.

Good for Microservices, Batch Processing, Immutable Infrastructure...?

Operationalized and Orchestration.

![Docker Flow](https://dl.dropboxusercontent.com/u/6815194/Notes/docker_flow.png)

* [**docker-gen**](https://github.com/jwilder/docker-gen)
* [**Your very own server with Docker**](http://erwyn.piwany.com/your-very-own-server-with-docker/)
* [**Using OverlayFS with Docker on Ubuntu**](http://blog.thestateofme.com/2015/03/09/using-overlay-file-system-with-docker-on-ubuntu/)
* [**buildpack-deps**](https://github.com/docker-library/buildpack-deps/blob/master/jessie/Dockerfile)
* [**Docker patterns**](http://www.hokstad.com/docker/patterns)
* [**gosu**](https://github.com/tianon/gosu)
* [**Run your own registry with S3 as storage**](http://blog.programster.org/2015/03/17/run-your-own-private-docker-registry/)
* [In Tech We Trust Podcast](http://intechwetrustpodcast.com/)
* [Century Link Labs](http://www.centurylinklabs.com/)
* [Flynn](https://flynn.io/)
* [DEIS - PaaS](http://deis.io/)
* [drone.io](https://drone.io/)
* [Shippable](https://www.shippable.com/)
* [Shipward](http://shipyard-project.com/)
* [Panamax: Docker Management](http://panamax.io/)
* [Are docker users migrating to Ansible?](http://thenewstack.io/are-docker-users-migrating-to-ansible-and-away-from-puppet-and-chef/)
* [Nigel Poulton](http://blog.nigelpoulton.com/)
* [Adaptive IT Blog](http://blog.ingineering.it/)
* [Docker in production - Jérôme Petazzoni](https://www.youtube.com/watch?v=Glk5d5WP6MI)
* [Skydock - DNS for docker](https://github.com/crosbymichael/skydock)
* [Service registry bridge for Docker](https://github.com/progrium/registrator)
* [Overlay network](https://github.com/coreos/flannel)
* [dotScale 2013 - Solomon Hykes - Why we built Docker](https://www.youtube.com/watch?v=3N3n9FzebAA)
* [Fig and Panamax](http://panamax.io/)
* [Digital Ocean docker tutorial series](https://www.digitalocean.com/community/tutorial_series/the-docker-ecosystem)
* [Adopting Microservices at Netflix: Lessons for Architectural Design](http://nginx.com/blog/microservices-at-netflix-architectural-best-practices/)
* [Docker Hype](http://iops.io/blog/docker-hype/)
* [Docker vs Reality](http://www.krisbuytaert.be/blog/docker-vs-reality-0-1)
* [Separation Anxiety: A tutorial for isolating your system with Linux namespaces](http://www.toptal.com/linux/separation-anxiety-isolating-your-system-with-linux-namespaces)
* [Running Jenkins](http://www.catosplace.net/blog/2015/02/11/running-jenkins-in-docker-containers/)
* [Flocker](https://github.com/clusterhq/flocker)
* [Powerstrip](https://github.com/ClusterHQ/powerstrip)
* [Weave](https://github.com/zettio/weave)
* [docker exec is your boss](http://standalonex.com/docker-exec-is-your-boss/)
* [Deep dive into Docker storage drivers](http://jpetazzo.github.io/assets/2015-03-03-not-so-deep-dive-into-docker-storage-drivers.html#1)
* [An alerting dashboard for Graphite](https://github.com/scobal/seyren)
* [Scaling engineering with Docker](http://tech.gc.com/scaling-engineering-with-docker/)
* [On-demand activation of Docker containers with systemd](https://developer.atlassian.com/blog/2015/03/docker-systemd-socket-activation/)
* [invoke-rc.d???](http://jpetazzo.github.io/2013/10/06/policy-rc-d-do-not-start-services-automatically/)
* [Comment is good on Chef vs Docker](https://blog.relateiq.com/why-docker-why-not-chef/)
* [10 Docker tips and tricks](http://nathanleclaire.com/blog/2014/07/12/10-docker-tips-and-tricks-that-will-make-you-sing-a-whale-song-of-joy/)
* [docker inspect -f](http://container-solutions.com/2015/03/docker-inspect-template-magic/)

```
docker version
docker info
docker -v

▶ rpm -ql docker
▶ dpkg-query -L lxc-docker

/usr/bin/docker
/etc/bash_completion.d/docker
/etc/udev/rules.d/80-docker.rules
/usr/share/man/man1/

// Find out how much containers
// The AuFS mount-point for a container is
// `/var/lib/docker/aufs/mnt/$CONTAINER_ID/`
▶ sudo du -sh /var/lib/docker
▶ df -h /var/lib/docker
```

2-3% CPU utilization is very typical of a single server. Hypervisor changed that to increase more usage per machine. Container can change it even further.

Think in terms of "Services" and not processes. Think services, not your physical server. Physical server can come and go. Think of your server as virtual!

Making services do what you want in an automatable, API'able manner is a precursor for the DevOps notion of continuous deployment.

Disruptor: Continuous delivery with containerized microservices.
Microservices: Loosely coupled SOA with bounded contexts.
Ephemeral: Container is dump. Spin and terminate. Log elsewhere! DB elsewhere!

It's important to understand that it is far simpler to manage Docker if you view it as **role-based** VM rather than as deployable single-purpose processes. Go for role-based containers (app, db, cache, etc.)

## Image - Build --tag

Containers are nothing. It is already too late to do anything at run-time. Images are the "shippable" units and where it matters most.

Where can you get your images?

1. Docker Hub
2. quay.io
3. Your own private registry
4. Manually load image from Amazon S3 store
5. Build it yourself using Dockerfile

Prep your images to make it faster.

* [Docker Image Specification v1.0.0](https://github.com/docker/docker/blob/master/image/spec/v1.md)
* [Phusion baseimage-docker](https://github.com/phusion/baseimage-docker)
* [Docker and the PID 1 zombie reaping problem](https://blog.phusion.nl/2015/01/20/docker-and-the-pid-1-zombie-reaping-problem/)
* [ADD does not honour USER](https://github.com/docker/docker/issues/6119)
* [Caching and `apt-get update`](https://github.com/docker/docker/issues/3313)
* [Dockerfile Best Practices - take 2](http://crosbymichael.com/dockerfile-best-practices-take-2.html)
* Instructions like `ADD` are not cache friendly. `ADD` stuff as late as possible in the Dockerfile.
* [Amazon S3 registry](https://github.com/dogestry/dogestry)
* [Docker tricks of the trade and best practices thoughts](http://www.carlboettiger.info/2014/08/29/docker-notes.html)
* [Understanding Docker cache for faster builds](http://thenewstack.io/understanding-the-docker-cache-for-faster-builds/)
* [**Security best practices for Dockerfile**](http://linux-audit.com/security-best-practices-for-building-docker-images/)
* [**Dockerfile best practices**](https://github.com/docker/docker/blob/master/docs/sources/articles/dockerfile_best-practices.md)

A Docker image is made up of filesystem layered over each other. First layer is the `bootfs` and next layer is the `rootfs`. More filesystem will be union mounted to appear as one filesystem. Docker calls each of these filesystems images.

```
docker commit
docker images
docker rmi
docker save
docker search
docker tag
docker build
docker build -f other_Dockerfile
docker pull (Preemptively pull down images)
```

One of the reasons Docker is so lightweight is because of these layers. When you change a Docker image, like update an application to a new version, a new layer gets built. Thus, rather than replacing the whole image or entirely rebuilding, only that layer is added or updated. You don't need to distribute a whole new image, just the update, making it faster and simpler.

### Building our own images

2 ways to do it:

1. Use `docker commit`
2. Use Dockerfile with `docker build` (Recommended)

Dockerfile is recommended because it provides a more repeatable, transparent, and idempotent mechanism for creating images.

Where you put the Dockerfile is where Docker will get its context or build context from. Do not use `/` as your build directory. Use `.dockerignore` to keep the image small and the build fast by decreasing the chance of cache busting. See [Issue#2224](https://github.com/docker/docker/issues/2224)

Each instruction in Dockerfile is a new layer. Docker runs the container, perform the instruction, commit it and stop it. Then repeat the whole process again for the next instruction. When all instructions have been executed, the intermediate containers will get removed to clean things up.

127 layer limits.

* [Dockerfile builder reference](http://docs.docker.com/reference/builder/)
* [Optimizing your Dockerfile](http://tech.paulcz.net/2015/03/optimizing-your-dockerfiles/)

Embrace reusability in Dockerfile. Write general requirements early (make use of cache container), commit and name relevant checkpoints, leave customisations last.

The `RUN` is for build-time and `CMD` is for run-time.

Don't treat your Dockerfile like a bash script.

Sort your commands by frequency of change, the time it takes to run the command and how sharable it is with other images.

```dockerfile
FROM <base_image>
MAINTAINER mech "tech1@jobline.com.sg"
RUN apt-get update && \
    apt-get install -y nginx

RUN mkdir -p /var/www/html

# 2 environment variable to save layer space
# These ENVs are persisted into container
ENV SMTP_PORT 250 HTTPD_PORT 80

# If end in /, then it is a directory
# If archive, will be unpack
ADD latest.tar.gz /var/www/latest/

# Similar to ADD, but no extraction capabilities
COPY conf.d/ /etc/apache2/

# Change working directory to run the instructions
WORKDIR /opt/webapp/db
RUN bundle install
WORKDIR /opt/webapp
ENTRYPOINT ["rackup"]

# A marker that says these are my mount points from native host or other containers
VOLUME ["/opt/project", "/data"]

# Use array syntax is better than string
# RUN will not record state of processes nor will it automatically start daemons
# Use CMD or ENTRYPOINT to start daemons
# CMD can be overridden at run-time
# Only 1 CMD, if your want more, see supervisor
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]

# Or even better, combine them
# The CMD and ENTRYPOINT instructions work best when used together
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-h"] # Print help and allow overrides

EXPOSE 80 443
```

Always do clean up to keep the containers lean. Use standard package if possible.

After the `Dockerfile` definition is ok, you can build it:

`docker build -t "repository/image_name:tag" .`

Do not forget the "period" as the current context for the build.

To skip the cache, especially when you are debugging, you can use `--no-cache` when running `docker build`. This can be useful when you do not want to cache the `apt-get update` layer.

To prevent containers during build use the `docker build -rm`??

You can also build from a git source:

`docker build -t "x/y" https://github.com/x/y`

With Docker 1.5, you can now used named Dockerfile:

`docker build -f <docker-file> <docker-context-root-dir>`

### ONBUILD

The `ONBUILD` instruction is a trigger. It sets instructions that will be executed when another image is built from the image being build. This is useful for building images which will be used as a base to build other images.

`ONBUILD` is only useful for images that are going to be built `FROM` a given image. You would typically use `ONBUILD` for a language stack image that builds arbitrary user software written in that language with the Dockerfile.

See [Rails](https://registry.hub.docker.com/_/rails/) ONBUILD example

Images built from `ONBUILD` should get a separate tag.

```
ONBUILD ADD . /app/src
```

`ONBUILD` can't be used to trigger `FROM` and `MAINTAINER` instructions.

### Clean up

If a Docker build fails, Docker does not clean up the intermediate containers built up until that point. Docker treats the intermediate containers as build cache. Make sure you perform all package installations and software compilations before you `ADD` folders.

A good strategy is to tag your final built container so that it gets added to the Docker's image list. A tagged image which appear in the image list is a fully self-contained container which can then be used to seed new containers.

```
▶ docker rmi -f $(docker images | grep "^<none>" | awk '{print $3}')

// Remove all stopped containers
▶ docker rm $(docker ps -a | grep Exited | awk '{print $1}')
▶ docker rm -v $(docker ps -a -q -f status=exited)
	
// Clean up un-tagged docker images
▶ docker rmi $(docker images -q --filter "dangling=true")
▶ docker rmi $(docker images -q -f dangling=true)

// Stop and remove all containers (including running containers!)
▶ docker rm -f $(docker ps -a -q)
```

We can have a bash script for deployment also (untested)

See [Automated deployment with Docker - Lesson learnt](http://www.hiddentao.com/archives/2013/12/26/automated-deployment-with-docker-lessons-learnt/)

```
#!/usr/bin/env bash
set -e

echo '>>> Get old container id'
CID=$(sudo docker ps | grep "project" | awk '{print $1}')
echo $CID

echo '>>> Building new image'
sudo docker built -t="mywebapp"

echo '>>> Stopping old container'
if [ "$CID" != "" ];
then
  sudo docker stop $CID  
fi

echo '>>> Restarting docker'
sudo service docker restart
sleep 5

echo '>>> Starting new container'
sudo docker run -p 433:433 -p 80:80 -d webapp
```

If there is POWER OUTAGE which leads to unclean shutdown, you may get unkillable container (ghosts) which should be fixed in Docker 0.9.

## Container - Run --name (Stateless, Ephemeral)

Container should be stateless and ephemeral. Configuration is state. Mount it rather than put into Dockerfile?

Inside `/var/lib/docker/containers`

When you `docker run`, a brand new container will be created. This can be unexpected.

Containers have existed in various forms since the mid-1990s. When you download an app to your Android phone to play Angry Birds, you aren't downloading a virtual machine that houses the application. You are downloading a container that keeps the application isolated so it doesn't mess up other apps on your phone, like the address book.

Docker is like the App Store of iOS. It has made software installation, compartmentalisation, and removal very simple.

```
docker attach
docker run
docker exec
docker kill (SIGKILL)
docker restart
docker rm
docker create
docker start
docker stop (SIGTERM)
docker stop $(docker ps -aq)
docker restart
docker stats
docker inspect
docker port <container_id/name> <container_exposed_port_number>
```

```
// Hello World of container
// -i = --interactive
// -t = --tty
// -m = --memory
// -d = --detach
// --name
▶ sudo docker run --name container_name -i -t -m 512m ubuntu /bin/bash
▶ exit
▶ sudo docker start container_name
▶ sudo docker attach container_name

// Replaces SSH
▶ sudo docker exec -i -t app bash
▶ sudo docker exec -d container_name touch /home/this_is_new_file
▶ sudo docker exec -it container_name /bin/bash

// Totally remove the container
▶ sudo docker rm container_name

// Return the ID of the last created container
▶ sudo docker ps -l -q
```

Inspect the container:

```
▶ docker inspect --format='{{.NetworkSettings.IPAddress}}' container_name
▶ docker inspect --format='{{.NetworkSettings.Bridge}}' container_name
▶ docker inspect --format='{{.NetworkSettings.Ports}}' container_name
▶ docker inspect --format='{{.HostConfig.Binds}}' container_name
▶ docker inspect --format='{{.State.Pid}}' container_name
```

### Container Restart Policy

`docker inspect` will show the number of container restarts since Docker 1.5.0.

## Operational Logistics

Logging, Backup, Metric, etc.

* [**logspout**](https://github.com/gliderlabs/logspout)
* [Gathering container metrics](http://jpetazzo.github.io/2013/10/08/docker-containers-metrics/)
* [Understanding metrics roll-ups, retention and graph resolution](http://support.metrics.librato.com/knowledgebase/articles/66838)
* [Service monitoring system and time series database](http://prometheus.io/)
* [SoundClouds Prometheus suited for containers](http://thenewstack.io/soundclouds-prometheus-monitoring-system-time-series-database-suited-containers/)
* [Good for backing up to Amazon S3](https://github.com/rlmcpherson/s3gof3r)
* [ELK log analysis](https://www.cloudgear.net/blog/2015/apache-log-analysis-with-kibana-docker/)
* [Container Advisor](https://github.com/google/cadvisor)
* [fluentd](http://www.fluentd.org/)
* [Docker and Logstash](https://denibertovic.com/post/docker-and-logstash-smarter-log-management-for-your-containers/)
* [The state of logging on Docker](https://blog.logentries.com/2014/03/the-state-of-logging-on-docker/)
* [Mount to log volume and use logrotate to manage it](http://0x74696d.com/posts/docker-logging/)
* [**Docker logs - aggregating with ease**](http://stackengine.com/docker-logs-aggregating-ease/)
* [Add log rotation signal handling to docker daemon - GitHub issue](https://github.com/docker/docker/issues/7333)

Logging (logstash, Kibana?), monitoring, and health management.

* cgroups give us per-container measurement
* Disable memory accounting
* No overhead if you run `--net host` for networking
* Log management: dump process logs to stdout and use a collection container like logspout
* Alternatively mount /dev/log into your container

For backup

```
▶ sudo docker run --name mysqldata -v /var/lib/mysql busybox true
▶ sudo docker run --name mysql --volumes-from mysqldata mysql
▶ sudo docker run --rm --volumes-from mysqldata mysqlbackup tar -clf /var/lib/mysql | stream-it-to-the-cloud.py
```

```
// A new style to do backup by Petazzoni
▶ docker run --name mysqldata -v /var/lib/mysql busybox true

// Start app container sharing that volume
▶ docker run --volumes-from mysqldata mysql

// Create a separate image with backup tools
// Dockerfile with
▶ apt-get install rsync s3cmd

// Use the special backup image
▶ docker run --rm --volumes-from mysqldata mysqlbackup tar -cJf- /var/lib/mysql | stream-it-to-the-cloud.py
```

```
// A new style to do log by Petazzoni

// Create a data container to hold the logs
▶ docker run --name logs -v /var/log busybox true

// Start app container sharing that volume
▶ docker run --volumes-from logs may

// Inspect logs
▶ docker run -it --volumes-from logs -w /var/log ubuntu bash
▶ docker run -it --volumes-from logs turbogrep

// Ship logs to somewhere else (logstash, syslog, splunk...)
▶ docker run --volumes-from log pipestash
```

## Script Makefile

```
GIT = pie/git
BUILD = pie/builder
IMAGE = pie/hubot

hubot:
  docker run --rm -v $(pwd):/opt:rw -e GPG=$$GPG $(GIT) /bin/bash -c "..."
hubot.tar: | hubot
  docker run --rm -v $(pwd)
clean:
  rm -rf hubot && rm -f hubot.tar
```

## Redis

## Postgres

## Sphinx

## Nginx

* [Deploying Nginx with Docker](http://nginx.com/blog/deploying-nginx-nginx-plus-docker/)
* [Some nginx example](http://curtisz.com/someone-set-us-up-the-docker/)

## Examples

* [Netflix OSS](https://hub.docker.com/u/netflixoss/)
* [Ghost blog and MariaDB with](http://blog.mewm.org/ghost-mariadb-with-docker-fig/)

## People

* [Brian Goff - @cpuguy83](http://container42.com/)
* [Nathan LeClaire](http://nathanleclaire.com/post/)

## Videos

* [Docker - A lot changed in a year - Feb 2015](https://www.youtube.com/watch?v=lCjp7AYCjCE)
* [Docker and SELinux](https://www.youtube.com/watch?v=zWGFqMuEHdw)
* [Docker 101](https://www.youtube.com/watch?v=4W2YY-qBla0)
* [Lightweight virtualization with LXC and Docker](https://events.yandex.ru/lib/talks/1085/)