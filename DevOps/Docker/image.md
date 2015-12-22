# Image

* [EJSON - managing secrets](https://github.com/Shopify/ejson)
* [Vault - managing secrets](https://github.com/hashicorp/vault)
* [A docker container to clean up your docker containers](http://ebarnouflant.com/posts/1-a-docker-container-to-clean-up-your-docker-containers)

Everything starts from the image. `Dockerfile` is just a text file. You have to build it to make an image. With that image, you can proceed to run it as a running container.

* Build - `docker build` from Dockerfile
* Ship - Push to registry (ignore it)
* Run - `docker run <image>`

## Filesystem Layers and Cache

Docker will use a local cache whenever possible. This can sometimes lead to unexpected issues. To disable it use: `no-cache` during `docker build`.

## Non-Privileged User

Even with isolation, containers still run on the host kernel. So for production container, always run under the context of a non-privileged user.

```
USER deploy
```

```
# Create postgres user and group with automatically assigned UID
# and GID
RUN groupadd -r postgres && useradd -r -g postgres postgres
```

However Postgres containers require elevated privileges during startup. Instead of using `sudo`, it uses `gosu` to start the postgres process as the postgres user. Doing so makes sure that the process runs without administrative access in the container.


## ONBUILD

Not all images contain applications. Some are built as platform for downstream images. The ability to "inject" downstream built-time behavior.

Typically use as a "base" for another "build".

The downstream Dockerfile will use this upstream Dockerfile (that has the ONBUILD instructions).

## Building

You can have many Dockerfiles for your single repository project.

The following ask docker to find `Dockerfile_web` as the `Dockerfile` and set where to find it at `docker_web` folder.

```
▶ docker build --tag jobline/web:cny --file Dockerfile_web ./docker_web
▶ docker build -t jobline/web:cny -f Dockerfile_web ./docker_web
▶ docker build -t jobline/web -f web.df
```

* [Dockerfile Reference](https://docs.docker.com/reference/builder/)
* [Best practices for Dockerfile](http://docs.docker.com/articles/dockerfile_best-practices/)

### ADD

Include files from local filesystem into the image. Once image is built, the local filesystem does not matter anymore.

Different from `COPY` in that it will fetch remote URL files + doing unzipping of archive files.

```
ADD ["./live-impl", "${APP_ROOT}"]
```

### COPY

Any files copied will be set to `root` ownership! Therefore it is better to delay any `RUN` instructions to change file ownership until all of the files have been copied into the image.

```
COPY ["file1", "file2", "destination_folder"]
COPY "source" "destination"
COPY "source_folder" "destination_folder"

# Okay to use shell-style
COPY conf.d/ /etc/apache2/

# Better to use exec-style
COPY ["conf.d/", "/etc/apache2/"]
```

### VOLUME

Defining volumes at image build time is more limiting than at runtime. You have no way to specify a bind-mount volumes or read-only volumes at image build time.

### ENV

Any safe environment variables can be stored inside your Dockerfile. Unless it is secret which should be run at runtime.

```
# Only use up 1 layer
ENV APP_ROOT=/production/jobline \
    VERSION=6 \
    POSTMARK_API_KEY=???
```

You can access your ENV inside the Dockerfile using `${POSTMARK_API_KEY}` in string or `$POSTMARK_API_KEY` elsewhere for example.
	
To know for sure you ENV are there, you can `docker inspect <image>`### ENTRYPOINT and CMD

The default `ENTRYPOINT` for a container is `/bin/sh` and `CMD` actually represents an argument list for the `ENTRYPOINT`.

