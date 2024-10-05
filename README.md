# Docker

There's a lot of depth to be found in docker.

To truly utilize docker you want to use docker-compose.
But often the important part is knowing how to specify information, this is where the cheat sheet comes into play.

### The basic compose:

<details> 
  <summary>Basic compose: </summary>
Its very basic...


```
version: ${VERSION}

services:
  container:
    container_name: ${NAME}
    restart: unless-stopped
    image: ${IMAGE}:${VERSION}
    ports:
     - ${PORT}:${PORT}
```
<details> 
  <summary>Variable explanation: </summary>
  
`VERSION:` This indicates the docker-compose version to use.

`NAME:` Specifies the name of the container

`IMAGE:` What image the container uses.

`VERSION:` The version of the specified image, can always use "latest".

`PORT:` To enable network traffic over certain ports use this.
</details>
</details>

### The networked compose:

<details> 
  <summary>Basic compose: </summary>
Its connected!


```
version: ${VERSION}

services:
  container:
    container_name: ${NAME}
    restart: unless-stopped
    image: ${IMAGE}:${VERSION}
    ports:
     - ${PORT}:${PORT}

    networks:
      logging-network:
        ipv4_address: ${IP_ADDRESS}
        gateway: ${GATEWAY_ADDRESS}
    dns:
      - ${DNS}
```
<details> 
  <summary>Variable explanation: </summary>
  
`VERSION:` This indicates the docker-compose version to use.

`NAME:` Specifies the name of the container

`IMAGE:` What image the container uses.

`VERSION:` The version of the specified image, can always use "latest".

`PORT:` To enable network traffic over certain ports use this.

`IP_ADDRESS:` ip-address of the container, remove to use first available.

`GATEWAY_ADDRESS:`Gateway of the network, remove to use default.

`DNS:`Set a custom DNS server for this specific container.
</details>
</details>
