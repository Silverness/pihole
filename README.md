# pihole

## Raspberry Pie

To start a container on the remote raspberry pi

```bash
$ docker-compose --context remote-pi up -d
```

### SSH into the pi-hole

```bask
ssh {username}@{ipAddress}
```

## Update Pie Hole

Using docker compose to update a container running on a remote hose (raspberry pi).

1. Figure out the remote context to run the update.

```bash
docker context ls
```

2. Update remote docker images

```bash
docker-compose --context {contextName} pull
```

3. Start the container

```bash
docker-compose --context remote-pi up -d
```

## Reset Pi-hole web user password

1. Attach to the running container on the Raspberry pi

```bash
docker --context {contextName} exec -it <container> bash
```

2. Run Password reset command

```bash
sudo pihole -a -p
```

## Links

[Github](https://github.com/pi-hole/docker-pi-hole)

[Walk Through](https://burakkarakan.com/blog/pihole-on-raspberry-using-pi-docker-and-docker-compose/)

[Docker Remote](https://www.docker.com/blog/how-to-deploy-on-remote-docker-hosts-with-docker-compose/)

[Firebog](https://firebog.net/)

[Pi-hole Docker](https://visibilityspots.org/dockerized-cloudflared-pi-hole.html)