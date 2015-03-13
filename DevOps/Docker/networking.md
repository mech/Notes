# Networking

Containers have their own internal network and IP address as proven by `docker inspect`.

* [**Network configuration - More advanced**](https://docs.docker.com/articles/networking/)
* [**Introducing Linux Network Namespaces**](http://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/)
* [Network port mapping](http://docs.docker.com/userguide/dockerlinks/#network-port-mapping-refresher)
* [Socketplane - Instead of using docker0, use Open vSwitch](http://www.socketplane.io/)
* [Overriding Docker DNS in case you need to for SingNet](http://blog.markrendle.net/a-quick-note-on-docker-dns-resolution/)
* [Multi-host Docker network](http://wiredcraft.com/blog/multi-host-docker-network/)

By default the `-p` flag will bind the port to all interfaces on the host (`0.0.0.0`). The `-p` flag can be used multiple times to configure multiple ports.

Binding specific IP and port:

```
// Publish port 80 of the container to localhost of the host with a
// static port to 80
▶ sudo docker run -d -p 127.0.0.1:80:80 --name jobline_web jobline/nginx

// Bind to dynamic port with empty `:`
▶ sudo docker run -d -p 127.0.0.1::5000 nginx

▶ sudo docker port webapp 80
▶ sudo docker port redis
```

The `-p` flag can be used multiple times to configure multiple ports like 80 and 443.

### Linking

Besides network port mappings, you can communicate with other containers through Docker linking system.
	
Container names have to be unique. If you want to re-use a container name you must delete the old container with `docker rm` before you can create a new container with the same name. You can also use `--rm` which will delete the container immediately after it is stopped.

```
▶ sudo docker run
    -p 4567           # So we can access our webapp externally
    --name webapp     
    --link redis:db   # container_name:alias_name
    -t
    -i
    -v $PWD/webapp:/opt/webapp
    local/sinatra

▶ sudo docker ps -l
▶ sudo docker inspect -f "{{ .Name }}" <container_id>
```

The `--link` flag setup a parent-child link between 2 containers.

No need to `-p` because parent can communicate to any open ports on the child container.

**Note**: Linking only works on a single Docker host. You can't link between containers on separate Docker hosts. For multi-host and cross-host linking, you need to do orchestration/clustering/discovery.

With the linking, you can find it at: `/etc/hosts` and ENV variables.

```
172.17.0.11	916f09cd3281
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
...
172.17.0.5	db

// database.yml
production:
  adapter: postgresql
  encoding: unicode
  username: postgres
  password:
  host: db
```

You can then `ping db` or use it for your application source code. Or you can use `ENV['DB_PORT']` or `ENV['DB_PORT_4567_TCP_ADDR']`.

`DB_PORT` is just a very convenient first port Docker provided for you.

You can run `env` on the `webapp` container to find out all the environment variables.

```
DB_NAME=/webapp/db
DB_PORT=tcp://172.17.0.5:4567
DB_PORT_4567_TCP_ADDR=172.17.0.5
DB_PORT_4567_TCP_PORT=4567
DB_PORT_4567_TCP_PROTO=tcp
```

**Note**: If source container is restarted, the IP address in the environment variables are not automatically updated. So if you want to configure your application, it is better to use the `/etc/hosts` entries for IP address.

If you disable icc via `--icc=false`, container A cannot access container B unless explicitly allowed via a link. This is a huge win for securing your containers.

## docker0

Every Docker container is assigned an IP address though the `docker0` interface.

```
▶ ip a show docker0
▶ brctl show docker0
▶ ip -f inet a

▶ sudo iptables -L -n
▶ sudo iptables -t nat -L -n
```

`docker0` is a virtual switch created entirely in software.

Inside your container when you do `mount`

```
▶ mount
/dev/disk/by-uuid/f9868a3d on /etc/resolv.conf type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/disk/by-uuid/f9868a3d on /etc/hostname type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/disk/by-uuid/f9868a3d on /etc/hosts type ext4 (rw,relatime,errors=remount-ro,data=ordered)
```

Is it better to set `--icc=false` and just using linking to let containers communicate with each other?

## Static IP Addresses

Fixed IP on a container is a hard issue.

* [Docker container changes IP upon restart](https://github.com/docker/docker/issues/2801)
* [Allow users to specify an IP for their container](https://github.com/docker/docker/issues/6743)
* [Pipework](https://github.com/jpetazzo/pipework)
* [How to configure Docker to start containers on a specific IP address range](http://jpetazzo.github.io/2013/10/16/configure-docker-bridge-network/)