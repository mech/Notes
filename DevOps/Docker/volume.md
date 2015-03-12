# Volume

AuFS `mount()` is fast, so creation of containers is quick. But initial `open()` is expensive when writing big files like databases. We ended up putting all important data on volumes.

* [Overview of storage scalability in Docker](http://developerblog.redhat.com/2014/09/30/overview-storage-scalability-docker/)
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

When do you use `-v` and when do you use `--volumes-from`? 

When you mount using the `-v` option, you can then use that on other container using the `--volumes-from` flag. It really depends on how you organise your volumes.

Should we use `ADD` instruction instead of volumes to house application code?

## Data Containers

When Docker updates a container, it doesn't apply a patch or update, it rebuilds the entire container. You use Dockerfile to add the applications and components you need. So how the heck are you supposed to use a database then? Can't really afford to wipe that data.

* [How to deal with persistent storage](http://stackoverflow.com/questions/18496940/how-to-deal-with-persistent-storage-e-g-databases-in-docker)
* [Data-only container pattern](http://www.tech-d.net/2013/12/16/persistent-volumes-with-docker-container-as-volume-pattern/)
* [Advanced Docker volumes](http://crosbymichael.com/advanced-docker-volumes.html)
* [Tiny Docker pieces, loosely joined](http://www.offermann.us/2013/12/tiny-docker-pieces-loosely-joined.html)
* [Portable volumes using just the Docker CLI](https://clusterhq.com/blog/powerstrip-flocker-portable-volumes-using-just-docker-cli/)
* [Persistent data with Docker](http://www.offermann.us/2013/12/tiny-docker-pieces-loosely-joined.html)
* [Why Docker data containers are good](https://medium.com/@ramangupta/why-docker-data-containers-are-good-589b3c6c749e)
* [What is the best way to manage permissions for Docker shared volumes](http://stackoverflow.com/questions/23544282/what-is-the-best-way-to-manage-permissions-for-docker-shared-volumes)
* [Lightbulb moment with Docker](http://magicalyak.org/2015/02/05/lightbulb-moment-with-docker/)

Can share folders with host by bind mounting as well as share folders with other container through `--volumes-from`.

The data-only container is run on a baritone image and actually does nothing except exposing a data volume.

Mounting data directories directly from the host is considered a hack, which can useful in specific situations but should be avoided unless you know for sure you can't do it any other way. The biggest reason is to preserve portability, which is the reason Docker is useful in the first place.

When you type a command which requires Docker to mount a directory from the host, the result of that command depends on your particular host.

This problem is amplified by the fact that bind-mounts do not abstract ownership and permission bits.
