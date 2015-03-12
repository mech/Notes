# Docker Cluster

* [Benefits of Docker for application deployment](http://knitatoms.net/2013/12/benefits-of-docker-for-application-deployment/)

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



Discoverd
Ambassadord
Registrator
Consulate
Duplex
Configurator