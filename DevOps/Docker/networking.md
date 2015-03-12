# Networking

* [Network port mapping](http://docs.docker.com/userguide/dockerlinks/#network-port-mapping-refresher)
* [Network configuration - More advanced](https://docs.docker.com/articles/networking/)
* [Socketplane - Instead of using docker0, use Open vSwitch](http://www.socketplane.io/)
* [Overriding Docker DNS in case you need to for SingNet](http://blog.markrendle.net/a-quick-note-on-docker-dns-resolution/)
* [Multi-host Docker network](http://wiredcraft.com/blog/multi-host-docker-network/)

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