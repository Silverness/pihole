# PiHole

## Raspberry Pie

- Creates a private network inside docker compose called pihole_net
- Spins up a container with cloudflared running on port 5054 and IP address 10.0.0.2
- Spins up a container with Pi-Hole and IP address 10.0.0.3

### Update Raspberry Pie OS

1. SSH into Pi as admin

    ```bash
    ssh {username}@{ipAddress}
    ```

2. Update the repository package list

    ```bash
    sudo apt update
    ```

3. Upgrade all packages

    ```bash
    sudo apt full-upgrade
    ```

4. Clean up .deb packages (Optional)

    ```bash
    sudo apt clean
    ```

5. Restart

    ```bash
    sudo reboot
    ```

## Docker on RaspberryPi

To start a container on the remote raspberry pi

  ```bash
  docker-compose --context remote-pi up -d  
  ```

### Update Pie Hole & Cloud Flared

Using docker compose to update a container running on a remote hose (raspberry pi).

1. Figure out the remote context to run the update.

    ```bash
    docker context ls
    ```

2. Update remote docker images.

    ```bash
    docker-compose --context {contextName} pull
    ```

3. Start the container

    ```bash
    docker-compose --context remote-pi up -d
    ```

### Reset Pi-hole web user password

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
[Pi-hole and cloudflared with Docker](https://mroach.com/2020/08/pi-hole-and-cloudflared-with-docker/#pi-hole-and-cloudflared-relationship)
