# docker-wordpress-nginx-ssh

[![Deploy to Tutum](https://s.tutum.co/deploy-to-tutum.svg)](https://dashboard.tutum.co/stack/deploy/)

This is basically a clone of the current docker container provided by [tlongren](https://github.com/tlongren/docker-wordpress-nginx-ssh). The only feature that was added is the hability to use sudo.

A Dockerfile that installs the latest wordpress, nginx, php-apc and php-fpm, and openssh. Based heavily on [this](https://registry.hub.docker.com/u/oskarhane/docker-wordpress-nginx-ssh/).

## Installation

The easiest way get up and running with this docker container is to pull the latest stable version from the [Docker Hub Registry](https://registry.hub.docker.com/u/zatarra/docker-wordpress-nginx-ssh/):

```bash
$ docker pull zatarra/docker-wordpress-nginx-ssh:latest
```

If you'd like to build the image yourself:

```bash
$ git clone https://github.com/zatarra/docker-wordpress-nginx-ssh.git
$ cd docker-wordpress-nginx-ssh
$ sudo docker build -t="zatarra/docker-wordpress-nginx-ssh"
```

## Usage

The -p 80:80 maps the internal docker port 80 to the outside port 80 of the host machine. The other -p sets up sshd on port 2222.

```bash
$ sudo docker run -p 80:80 -p 2222:22 --name docker-name -d zatarra/docker-wordpress-nginx-ssh:latest
```

Start your newly created container, named *docker-name*.

```
$ sudo docker start docker-name
```

After starting the container docker-wordpress-nginx-ssh checks to see if it has started and the port mapping is correct.  This will also report the port mapping between the docker container and the host machine.

```
$ sudo docker ps

0.0.0.0:80->80/tcp, 3306/tcp, 0.0.0.0:2222->22/tcp
```

You can then visit the following URL in a browser on your host machine to get started:

```
http://127.0.0.1:80
```

You can also SSH to your container on 127.0.0.1:2222. The default password is *wordpress*, and can also be found in .ssh-default-pass.

```
$ ssh -p 2222 wordpress@127.0.0.1
```

Now that you've got SSH access, you can setup your FTP client the same way, or the SFTP Sublime Text plugin, for easy access to files.


You can view logs like this:

```
$ sudo docker logs docker-name
```

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/zatarra/docker-wordpress-nginx-ssh/trend.png)](https://bitdeli.com/free "Bitdeli Badge")
