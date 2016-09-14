# nginx-proxy-letsencrypt
Docker compose file for nginx-proxy and Let's encrypt containers

## A note about networks
V2 docker compose files either create a default network named from the directory the compose file is run from, or named networks as specified in a compose file.

This enables great flexibility in establishing networks between containers that need to talk to one another while not exposing containers to traffic that is unnecessary or unsafe.

The trick with the nginx reverse proxy is that it can only proxy containers it is on a network with. So the nginx container needs to be added to those networks it needs to proxy for using the following command:
docker network connect your-network-name nginx-proxy

Also of note, is that if containers have been started in other ways that a compose file, docker run commands for instance, they will be part of a network called bridge. The proxy container will need to be added to this network if it is not already.

The docker inspect container-name command will list, amongst other things, the networks a container is currently attached to.

The docker network ls command will list default and user-added networks.

The docker network inspect network-name will list, amongst other things, containers attached to a network.
