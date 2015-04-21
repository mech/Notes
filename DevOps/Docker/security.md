# Security

* [Disable SUID programs](http://blog.tutum.co/2015/02/03/hardening-containers-disable-suid-programs/)
* [Docker security tuning](https://opensource.com/business/15/3/docker-security-tuning)
* [Docker and SELinux](https://www.youtube.com/watch?v=zWGFqMuEHdw)
* [Make container reliable](http://blog.jelastic.com/2015/04/14/5-key-features-make-containers-reliable-production-applications/)
* Treat container services just like regular services. Drop privileges as quickly as possible. Do not run Nginx web server as root.
* Use read-only mount points like `/sys`, `/proc/sys`.
* Use capabilities to drop CAP_XX to minimize attack surface.
* Remove network namespace for database container because maybe you don't need it.
* SELinux protect the host system from container processes
* Container processes only write to container files

The `~/.dockercfg` configuration file holds Docker registry authentication credentials, so protect this file! It should be owned by your user with permissions of `0600`

Breaking out of a container requires root privilege.

```
// Using `adduser` in Dockerfile
// Start a container as non-root user
▶ sudo docker run -u deploy
▶ sudo docker create -user deploy
```

## Capabilities

If your container did not change the UID/GID of any processes, you could drop these capabilities from your container, making it more secure.

```
▶ docker run -d --cap-drop SETUID --cap-drop SETGID --cap-drop FOWNER fedora /bin/sh
```
