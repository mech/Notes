# Container

* [Spring cleaning your container](http://odino.org/spring-cleaning-of-your-docker-containers/)

Containers are separated from the data, and therefore interchangeable and immutable and ephemeral.

```
// docker run is just like
▶ docker create // 1
▶ docker start  // 2

// At /var/lib/docker/containers/???
▶ cat config.json | python -m json.tool
▶ cat hostconfig.json | python -m json.tool
```

## docker run

```
// --rm to delete the container when it exits
// -t to allocate a psuedo-TTY
// -i to go into interactive session
// --restart=on-failure:3 to restart  maximum of 3 times only
▶ docker run -d --restart=on-failure:3 --name jobline_db -l deployer=mech postgres:latest
```

## docker ps

```
▶ docker ps -a -f label=deployer
```

## docker inspect

## docker exec

```
▶ docker exec -it 567656787 /bin/bash
```

## CPU pinning, shares and memory restriction

```
// 1024 is CPU share full pool, so 512 is half of the CPU time
// cpuset start from CPU core 0
▶ docker run --rm -it -c 512 --cpuset=0 ubuntu:latest
```

While CPU only impacts the application's priority for CPU time and is not a hard limit, the memory limit is a hard limit!

```
// Both RAM and swap space are 512MB
▶ docker run --rm -it -m 512m ubuntu:latest

// Disable swap completely
▶ docker run --rm -it -m 512m --memory-swap=-1 ubuntu:latest
```

## docker rm/rmi

```
// Use only when in development machine
▶ docker rm $(docker ps -a -q)
▶ docker rmi $(docker images -q -)

// To remove all containers that exited with a non-zero state
▶ docker rm $(docker ps -a -q --filter 'exited!=0')

// To remove all untagged images
▶ docker rmi $(docker images -q -f "dangling=true")
```


