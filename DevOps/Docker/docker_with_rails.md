# Docker with Rails

Maybe we install nginx on host that acts as a load balancer also. Then the downstream will all be containers.

Requirements:

* Ease of use
* Zero downtime - HAProxy with sticky session
* Automated
* Save your image to S3 and manually load them

During development, you might not want to build an image each time you iterate. So you use volumes for Polymorphic Container Pattern.

Make use of COW and caching? Build every time? Developer develop on their laptop. They build Dockerfile to specify their requirements. They push it to the registry. Production pull down from registry and essentially build it and run it.

Immutable Infrastructure - Build all the time? Completely replacing, instead of updating an existing part of your infrastructure makes your deployments less complex.

Deploy images, not infrastructure updates. No updates. Make it immutable.

Regular applications like MySQL, Nginx, Postgres, Redis, etc. never need any kind of root privilege. Don't run them as root! Ever!

Mounting configuration files.

* [Google/ruby?](https://registry.hub.docker.com/u/google/ruby/)
* [**Deploying with Mina**](https://medium.com/alliants-blog/deploying-web-apps-with-mina-and-docker-c840193eb4be)
* [**Rails app on Docker using Passenger image**](https://rossfairbanks.com/2015/03/06/rails-app-on-docker-using-passenger-image.html)
* [Some rails example](http://mwdesilva.com/posts/103-simple-scalable-infrastructure-with-digitalocean-terraform-and-docker)
* [**Deploy Rails app using Docker**](https://intercityup.com/blog/deploy-rails-app-including-database-configuration-env-vars-assets-using-docker.html)
* [**12 Factor**](http://12factor.net/)
* [**Open vSwitch**](http://openvswitch.org/)
* [**Zero Downtime Deployments with Docker**](https://www.youtube.com/watch?v=mQvIWIgQ1xg)
* [Zero downtime deployment of any web app with Docker and nginx](http://acroca.com/blog/2014/07/17/zero-downtime-deployment-of-any-web-app-with-docker-and-nginx.html)
* [**Production Deployment with Docker**](https://www.codeschool.com/blog/2015/01/16/production-deployment-docker/)
* [**docker-rails-dev**](https://github.com/pywebdesign/docker-rails-dev)
* [Finnlabs rails-docker](https://github.com/finnlabs/rails-docker)
* [passenger-docker](https://github.com/phusion/passenger-docker)
* [Deploying python with Docker](https://medium.com/@rlbaker/deploying-python-with-docker-15a472cf12a5)
* [Rails development using Docker and Vagrant](https://blog.abevoelker.com/rails-development-using-docker-and-vagrant/)
* [A week of Docker](http://danielmartins.ninja/posts/a-week-of-docker.html)
* [`$ ./jobline deploy`](https://github.com/fstephany/hello-pharo/blob/master/app)
* [Capistrano-like with Ansible](http://blog.versioneye.com/2014/09/24/rebuilding-capistrano-like-deployment-with-ansible/)
* [The why and how of Ansible and Docker](http://thechangelog.com/ansible-docker/)
* [ansible-docker](https://github.com/gerhard/ansible-docker)
* [Ansible & Docker - The path to Continuous Delivery](http://gerhard.lazu.co.uk/ansible-docker-the-path-to-continuous-delivery-1)
* [Dockerize a Rails app with Sidekiq](http://khanetor.com/2015/02/dockerize-a-rails-app-with-background-processing/)
* [Bash script for orchestration](https://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/)
* [Multi-tier architecture tutorial](http://jeff-davis.blogspot.sg/2015/02/multi-tier-architecture-tutorial-using.html)
* [Zero downtime deployments](http://docs.quay.io/solution/zero-downtime-deployments.html)
* [Tiller?](https://github.com/markround/tiller)
* [Ghost and MariaDB with Docker and Fig](http://blog.mewm.org/ghost-mariadb-with-docker-fig/)
* [Automate your dev workflow with Docker](http://blog.codeship.com/automate-your-dev-workflow-with-docker/)
* [What are the Steps to containerize my Monolithic App](https://www.joyent.com/blog/what-are-the-steps-to-containerize-my-monolithic-app)

We can write bash script to stop, start and update our environment. We can even write script to go into maintenance mode and remove scheduled jobs first for FM to restart.

**Tips**: Pass the Rails env in via the `docker` command and mount the config directory as a volume.

```
# File: docker-build.sh
# This script will remove old builds and create a brand new one
docker rm -f $(docker ps -aq) # Remove all non-running containers

# Clean up orphaned images by deleting untagged images
docker rmi -f $(docker images | grep "^<none>" | awk '{print $3}')
docker rmi local/nginx-rails-passenger

# --rm will remove intermediate containers after a successful build
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

```
MINECRAFT=$(docker run -d minecraft)
MAPSERVER=$(docker run -d mapserver)

docker run --volumes-from $MINECRAFT --volumes-from $MAPSERVER mapgenerator

// Put it in cron
@hourly docker run --...
```

## Application Configuration

At the host, prepare your `jobline_app_config` to include secrets and other API keys.

```
// Use --env-file to separate secrets
▶ docker run -d -t --env-file jobline_app_config nginx
```

