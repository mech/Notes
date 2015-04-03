# Docker Cluster

* [Benefits of Docker for application deployment](http://knitatoms.net/2013/12/benefits-of-docker-for-application-deployment/)
* [SDN, Docker and the Real Changes Ahead](http://thenewstack.io/sdn-docker-real-changes-ahead/)
* [SocketPlane == Open vSwitch + Consul + VXLAN + Docker](http://aucouranton.com/2015/01/16/docker-virtual-networking-with-socketplane-io/)
* [Setup networking using weave](http://xmodulo.com/networking-between-docker-containers.html)

VXLAN - extend the LAN.

DPDK accelerated OVS integration.

## Issues

* Wire up containers with links
* Wire up cross-host containers (Flocker?)
* Service discovery
* Planning and container creation (Bash script?)
* Backup strategy
* Database tuning

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

## Docker Compose

* [Don't stop containers when fig up exits](https://github.com/docker/compose/issues/741)
* [Data only containers / No run containers](https://github.com/docker/compose/issues/942)

Multi-container apps are a hassle.

* Build images from Dockerfiles
* Pull images from the Hub
* Configure and create containers
* Start and stop containers
* Stream their logs

## Container Orchestration

* [Fig is now docker-compose](http://chrisbarra.me/posts/docker-orchestration.html)
* [Crane - Lift containers with ease](https://github.com/michaelsauter/crane)
* [A Docker environment - See some bash scripts](https://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/)

Orchestration is collection of things. Not just a single thing.

SSH + systemd + etcd == Fleet (Overkill)

Discoverd
Ambassadord
Registrator
Consulate
Duplex
Configurator