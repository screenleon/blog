# Using Docker without sudo
> **Lien Chen** *2020-10-19*

* Let current useruse docker without sudo

```shell
$ # check if docker group exists
$ cat /etc/group | grep docker
docker:x:***:
$ # if it doesn't, create with this command:
$ #sudo groupadd docker

$ # add the current user to docker group
$ sudo usermod -a -G docker $MY_USER
$ # validate it
$ cat /etc/group | grep docker
docker:x:***:$MY_USER

$ # logout, and login again
```

[reference](https://dev.to/nabbisen/docker-without-sudo-34ci)