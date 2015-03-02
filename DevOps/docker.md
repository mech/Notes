# Docker

Tighten iteration loop.

OODA loop - Observe, Orient, Decide, Art. The one that win is the one that can go around this loop the fastest. Move the fastest, iterate the fastest.

Developer worries about what's "inside" the container. His code, libraries, package manager, apps and data. All Linux server to them look the same.

Ops worries what's "outside" the container. Login, remote address, monitoring, network config. All containers start, stop, copy, attach, migrate the same way.

Operationalized and Orchestration.

* [Docker Weekly](http://blog.docker.com/docker-weekly-archives/)
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
* [Flocker](https://github.com/clusterhq/flocker)
* [Fig and Panamax](http://panamax.io/)
* [Digital Ocean docker tutorial series](https://www.digitalocean.com/community/tutorial_series/the-docker-ecosystem)
* [Adopting Microservices at Netflix: Lessons for Architectural Design](http://nginx.com/blog/microservices-at-netflix-architectural-best-practices/)
* [Docker Hype](http://iops.io/blog/docker-hype/)
* [Docker vs Reality](http://www.krisbuytaert.be/blog/docker-vs-reality-0-1)
* [Separation Anxiety: A tutorial for isolating your system with Linux namespaces](http://www.toptal.com/linux/separation-anxiety-isolating-your-system-with-linux-namespaces)

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
▶ sudo du -sh /var/lib/docker
▶ df -h /var/lib/docker/
```

2-3% CPU utilization is very typical of a single server. Hypervisor changed that to increase more usage per machine. Container can change it even further.

Think in terms of "Services" and not processes. Think services, not your physical server. Physical server can come and go. Think of your server as virtual!

Making services do what you want in an automatable, API'able manner is a precursor for the DevOps notion of continuous deployment.

Disruptor: Continuous delivery with containerized microservices.
Microservices: Loosely coupled SOA with bounded contexts.
Ephemeral: Container is dump. Spin and terminate. Log elsewhere! DB elsewhere!

It's important to understand that it is far simpler to manage Docker if you view it as role-based VM rather than as deployable single-purpose processes. Go for role-based containers (app, db, cache, etc.)

## Image

Prep your images to make it faster.

* [Phusion](https://github.com/phusion/baseimage-docker)

A Docker image is made up of filesystem layered over each other. First layer is the `bootfs` and next layer is the `rootfs`. More filesystem will be union mounted to appear as one filesystem. Docker calls each of these filesystems images.

```
docker commit
docker images
docker rmi
docker save
docker search
docker tag
docker build
docker pull (Preemptively pull down images)
```

### Building our own images

2 ways to do it:

1. Use `docker commit`
2. Use `Dockerfile` with `docker build` (Recommended)

`Dockerfile` is recommended because it provides a more repeatable, transparent, and idempotent mechanism for creating images.

Where you put the `Dockerfile` is where Docker will get its context or build context from. Do not use `/` as your build directory.

Each instruction in `Dockerfile` is a new layer. Docker runs the container, perform the instruction, commit it and stop it. Then repeat the whole process again for the next instruction.

* [Dockerfile builder reference](http://docs.docker.com/reference/builder/)

Embrace reusability in Dockerfile. Write general requirements early (make use of cache container), commit and name relevant checkpoints, leave customisations last.

The `RUN` is for build-time and `CMD` is for run-time.

```
FROM <base_image>
MAINTAINER mech "tech1@jobline.com.sg"
RUN apt-get update
RUN apt-get install -y nginx

RUN mkdir -p /var/www/html

# 2 environment variable to save layer space
# These ENVs are persisted into container
ENV SMTP_PORT 250 HTTPD_PORT 80

# No question/dialog allowed
ENV DEBIAN_FRONTEND noninteractive

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

### ONBUILD

The `ONBUILD` instruction is a trigger. It sets instructions that will be executed when another image is built from the image being build. This is useful for building images which will be used as a base to build other images.

```
ONBUILD ADD . /app/src
```

`ONBUILD` can't be used to trigger `FROM` and `MAINTAINER` instructions.

## Container

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


## Networking

* [Network port mapping](http://docs.docker.com/userguide/dockerlinks/#network-port-mapping-refresher)
* [Network configuration - More advanced](https://docs.docker.com/articles/networking/)
* [Socketplane - Instead of using docker0, use Open vSwitch](http://www.socketplane.io/)

Binding specific IP and port:

```
▶ sudo docker run -d -p 127.0.0.1:80:80 --name jobline_web jobline/nginx

▶ sudo docker port webapp 80
▶ sudo docker port redis
```

The `-p` flag can be used multiple times to configure multiple ports like 80 and 443.

Every Docker container is assigned an IP address though the `docker0` interface.

```
▶ ip a show docker0
▶ brctl show docker0
▶ ip -f inet a
```

`docker0` is a virtual switch created entirely in software.

### Linking

```
▶ sudo docker run
    -p 4567           # So we can access our webapp externally
    --name webapp     
    --link redis:db   # container_name:alias_name
    -t
    -i
    -v $PWD/webapp:/opt/webapp
    local/sinatra
```

The `--link` flag setup a parent-child link between 2 containers.

No need to `-p` because parent can communicate to any open ports on the child container.

Note: Linking only works on a single Docker host. You can't link between containers on separate Docker hosts.

With the linking, you can find it at: `/etc/hosts` and ENV.

```
172.17.0.11	916f09cd3281
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
...
172.17.0.10	db
```

You can then `ping db` or use it for your application source code. Or you can use `ENV['DB_PORT']`

## Volume

* [Managing data in containers](http://docs.docker.com/userguide/dockervolumes/)
* Volumes are initialised when a container is created
* Changes to a volume are made directly
* Changes to a volume will not be included when you update an image
* Volumes persist (even when not running) until no containers use them (different from mounted host volume)
* Data volumes bypass the union file system. In other words, they are not captured by `docker commit`.
* It is possible to share a volume with a stopped container.

This allow us to add data (like source code), a database, log files, or other content into an image without committing it to the image and allows us to share that data between containers. Volume will not be included when we commit or build an image.

The VOLUME is just a directory that bypass the layered Union File System to provide shared data. It is different from mounting host directory. To mount host directory as volume, you need to do it at run-time:

```
// Mount host directory /src/webapp into container at /opt/webapp
// Use :ro for read-only mount
// The content inside /opt/webapp will be replaced by the host's one
▶ sudo docker run -d -v /src/webapp:/opt/webapp ubuntu

// Similar effect to VOLUME instruction
▶ sudo docker run -d -v /webapp ubuntu

// Create a named data volume container
// Purpose is just to share volume and not run application
// After that any the real DB container can --volumes-from to mount /dbdata
▶ sudo docker create -v /dbdata --name dbdata postgres
▶ sudo docker run -d --volumes-from dbdata --name db1 postgres

// More named data container examples
▶ sudo docker run -v /var/volume1 -v /var/volume2 --name DATA busybox true

// The following show how to backup your volume in
// --rm - remove the container when it exits
// It will backup to the current directory ($pwd)
// In the container, the backup file will be at /backup/bak.tar
// In the host, it will be at the current directory
// From the host, you can then do an Amazon S3 upload
▶ sudo docker run --rm --volumes-from dbdata -v $(pwd):/backup ubuntu tar cvf /backup/bak.tar /dbdata
```

When do you use `-v` and when do you use `--volumes-from`? In fact, that is the wrong question to ask. Both are used for the concept of volumes in general.

When you mount using the `-v` option, you can then use that on other container using the `--volumes-from` flag. It really depends on how you organise your volumes.

Should we use `ADD` instruction instead of volumes to house application code?

## Data Container

* [How to deal with persistent storage](http://stackoverflow.com/questions/18496940/how-to-deal-with-persistent-storage-e-g-databases-in-docker)
* [Data-only container pattern](http://www.tech-d.net/2013/12/16/persistent-volumes-with-docker-container-as-volume-pattern/)
* [Advanced Docker volumes](http://crosbymichael.com/advanced-docker-volumes.html)
* [Tiny Docker pieces, loosely joined](http://www.offermann.us/2013/12/tiny-docker-pieces-loosely-joined.html)
* [Portable volumes using just the Docker CLI](https://clusterhq.com/blog/powerstrip-flocker-portable-volumes-using-just-docker-cli/)


## Operational Logistics

* [Gathering container metrics](http://jpetazzo.github.io/2013/10/08/docker-containers-metrics/)
* [Understanding metrics roll-ups, retention and graph resolution](http://support.metrics.librato.com/knowledgebase/articles/66838)

Logging (logstash, Kibana?), monitoring, and health management.

* cgroups give us per-container measurement
* Disable memory accounting
* No overhead if you run `--net host` for networking

For backup

```
▶ sudo docker run --name mysqldata -v /var/lib/mysql busybox true
▶ sudo docker run --name mysql --volumes-from mysqldata mysql
▶ sudo docker run --rm --volumes-from mysqldata mysqlbackup tar -clf /var/lib/mysql | stream-it-to-the-cloud.py
```

## Security

* [Docker and SELinux](https://www.youtube.com/watch?v=zWGFqMuEHdw)
* Treat container services just like regular services. Drop privileges as quickly as possible. Do not run Nginx web server as root.
* Use read-only mount points like `/sys`, `/proc/sys`.
* Use capabilities to drop CAP_XX to minimize attack surface.
* Remove network namespace for database container because maybe you don't need it.
* SELinux protect the host system from container processes
* Container processes only write to container files

The `~/.dockercfg` configuration file holds Docker registry authentication credentials, so protect this file! It should be owned by your user with permissions of `0600`

## Docker Compose

Multi-container apps are a hassle.

* Build images from Dockerfiles
* Pull images from the Hub
* Configure and create containers
* Start and stop containers
* Stream their logs

## Container Orchestration

* [Fig is now docker-compose](http://chrisbarra.me/posts/docker-orchestration.html)
* [Crane - Lift containers with ease](https://github.com/michaelsauter/crane)

Orchestration is collection of things. Not just a single thing.

## Docker with Rails

Make use of COW and caching? Build every time? Developer develop on their laptop. They build Dockerfile to specify their requirements. They push it to the registry. Production pull down from registry and essentially build it and run it.

* [`$ ./jobline deploy`](https://github.com/fstephany/hello-pharo/blob/master/app)
* [Capistrano-like with Ansible](http://blog.versioneye.com/2014/09/24/rebuilding-capistrano-like-deployment-with-ansible/)
* [The why and how of Ansible and Docker](http://thechangelog.com/ansible-docker/)
* [ansible-docker](https://github.com/gerhard/ansible-docker)
* [Ansible & Docker - The path to Continuous Delivery](http://gerhard.lazu.co.uk/ansible-docker-the-path-to-continuous-delivery-1)
* [Deploy Rails app using Docker](https://intercityup.com/blog/deploy-rails-app-including-database-configuration-env-vars-assets-using-docker.html)
* [Dockerize a Rails app with Sidekiq](http://khanetor.com/2015/02/dockerize-a-rails-app-with-background-processing/)
* [12 Factor](http://12factor.net/)
* [Bash script for orchestration](https://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/)

We can write bash script to stop, start and update our environment. We can even write script to go into maintenance mode and remove scheduled jobs first for FM to restart.

```
# File: docker-build.sh
# This script will remove old builds and create a brand new one
docker rm -f $(docker ps -aq) # Remove all non-running containers

docker rmi -f $(docker images | grep "^<none>" | awk '{print $3}')
docker rmi local/nginx-rails-passenger

docker build --rm -t local/nginx-rails-passenger .
```

```
# docker-run.sh
# This script will just run docker without you have to type it always
docker run -d -p 80:80 -p 10022:22 --name jobline_web local/nginx /bin/sh /startup/docker-startup.sh
```

```
# docker-startup.sh
# Script to bring up services
/usr/sbin/rabbitmq-server &
/usr/sbin/sshd -D
```

## Examples

* [Netflix OSS](https://hub.docker.com/u/netflixoss/)

## Videos

* [Docker - A lot changed in a year - Feb 2015](https://www.youtube.com/watch?v=lCjp7AYCjCE)
* [Docker and SELinux](https://www.youtube.com/watch?v=zWGFqMuEHdw)
* [Docker 101](https://www.youtube.com/watch?v=4W2YY-qBla0)