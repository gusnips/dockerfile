dockerfile
==========

Dockerfiles for general use

## Enter a container

To enter a container or run commands in it, use [nsenter](https://github.com/jpetazzo/nsenter)

Install nsenter
```sh
    docker run --rm -v /usr/local/bin:/target jpetazzo/nsenter
```

Use docker-enter utility
```sh
    docker-enter my_awesome_container /bin/bash
```

or if you prefer manually, get the PID and then enter the container:

```sh
    PID=$(docker inspect --format {{.State.Pid}} <container_name_or_ID>)
    nsenter --target $PID --mount --uts --ipc --net --pid
```
