# Docker Cluster

Cluster (Swarm), Dynamic Scheduler (Mesos, Kubernetes)

* [Benefits of Docker for application deployment](http://knitatoms.net/2013/12/benefits-of-docker-for-application-deployment/)
* [SDN, Docker and the Real Changes Ahead](http://thenewstack.io/sdn-docker-real-changes-ahead/)
* [SocketPlane == Open vSwitch + Consul + VXLAN + Docker](http://aucouranton.com/2015/01/16/docker-virtual-networking-with-socketplane-io/)
* [Clocker - The Docker cloud maker](http://brooklyncentral.github.io/clocker/)
* [Calico - Pure Layer 3 Virtual Networking](http://www.projectcalico.org/)
* [Migrating MongoDB data with Mesos and Flocker](https://mesosphere.com/blog/2015/05/21/demo-migrating-mongodb-data-with-mesos-and-powerstrip/)
* [Jenkins, Packer, Kubernetes](http://googlecloudplatform.blogspot.com/2015/05/Automated-Compute-Engine-and-Docker-Image-Builds-with-Jenkins-Packer-and-Kubernetes.html)

VXLAN - extend the LAN.

DPDK accelerated OVS integration.

## Issues

* Wire up containers with links
* Wire up cross-host containers (Flocker?)
* Service discovery
* Planning and container creation (Bash script?)
* Backup strategy
* Database tuning

## Mesos

* [Mesos Sandbox using Docker Compose](https://spof.io/blog/2015/06/23/mesos-sandbox-using-docker-compose/)

## Calico

* [Project Calico Experiments](http://www.greenhills.co.uk/2015/05/22/projectcalico-experiments.html)
* [Docker networking using Project Calico](http://www.projectcalico.org/project-calico-at-the-docker-london-may-meetup/)

## Weave

* [Weave](https://github.com/weaveworks/weave)
* [Setup networking using weave](http://xmodulo.com/networking-between-docker-containers.html)
* [Using docker-machine with Weave 0.10](http://blog.weave.works/2015/04/22/using-docker-machine-with-weave-0-10/)


## Etcd

Backbone of a distributed system. Easily manage cluster coordination and state management - the source of truth.

etcd is consistent and partition tolerant in the CAP terms. It is "available" in the sense that data is available for reads when quorum is lost.

```
go get github.com/coreos/go-etcd/etcd
```

ZooKeeper, dozed and etcd are all similar in their architecture.

## Ambassador Patterns

* [Provide a way to dynamically link the containers](https://github.com/docker/docker/issues/3155)
* [Proposal: Network Driver](https://github.com/docker/docker/issues/9983)
* [Dynamic Docker links with an ambassador powered by etcd](https://github.com/tcnksm/docker-link-pattern/tree/master/coreos/dynamic-etcd-ambassador)

## docker-machine

* [Presenting Machine 0.2.0](https://www.youtube.com/watch?v=xwj44dAvdYo)

```
▶ docker-machine ls
▶ docker-machine create -d virtualbox dev
▶ eval "$(docker-machine env dev)"
▶ docker-machine env <machine_name>
▶ env | grep DOCKER

▶ docker-machine ssh dev

▶ docker-machine stop dev
▶ docker-machine start dev

▶ docker-machine rm dev
```

## Container Orchestration

Orchestration allow you to coordinate the **configuration** and **deployment** of your application onto multiple Docker daemons.

* [Fig is now docker-compose](http://chrisbarra.me/posts/docker-orchestration.html)
* [Crane - Lift containers with ease](https://github.com/michaelsauter/crane)
* [A Docker environment - See some bash scripts](https://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/)

Orchestration is collection of things. Not just a single thing.

SSH + systemd + etcd == Fleet (Overkill)

* Discoverd
* Ambassadord
* [Registrator](https://github.com/gliderlabs/registrator)
* Consulate
* Duplex
* Configurator