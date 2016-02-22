# Docker UI for managing docker images, containers and more

[Docker UI](https://github.com/crosbymichael/dockerui) is an awesome web UI project for working with docker from your browser. It lets you manage containers, images, networks and volumes from a pleasant UI. In addition to these management features, it lets you get a view of your docker histories such as graphing of containers and images created and information on container networks.

Running the docker ui is quite simple

```shell
$ docker run -d -p 9000:9000 --privileged -v /var/run/docker.sock:/var/run/docker.sock dockerui/dockerui
```

You need to make sure that you provide the appropriate path to the `docker.sock` as per your system's configuration.

You might want a [bash alias](https://github.com/techgaun/bash-aliases/blob/master/.bash_aliases) for running docker ui anytime you wish.
```shell
alias dockerui="docker run --rm -p 9000:9000 --privileged -v /var/run/docker.sock:/var/run/docker.sock dockerui/dockerui"
```
