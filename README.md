Assumptions:

- Platform is Mac
- You can run a docker container on platform

[Squid is running](https://github.com/sameersbn/docker-squid)

docker run --name squid -d --restart=always --publish 3128:3128 --volume /srv/docker/squid/cache:/var/spool/squid3 sameersbn/squid:3.3.8

[Squid accepts connections from local network](https://github.com/boot2docker/boot2docker/blob/master/doc/WORKAROUNDS.md)

VBoxManage controlvm "boot2docker-vm" natpf1 "tcp-port8000,tcp,,8000,,8000";

[Squid logs](https://github.com/sameersbn/docker-squid)

docker exec -it squid2 tail -f /var/log/squid3/access.log

[Squid instance IP]()

docker-machine ip default
