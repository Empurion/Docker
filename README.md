# Docker

There's a lot of depth to be found in docker.

To truly utilize docker you want to use docker-compose.
But often the important part is knowing how to specify information, this is where the cheat sheet comes into play.

### The basic compose:

The basic compose is just the minimal required and easiest way to run an container.


```
version: ${VERSION}

services:
  container:
    container_name: ${NAME}
    restart: unless-stopped
    image: ${IMAGE}:${VERSION}
    ports:
     - ${PORT]:${PORT}
```

`VERSION:` This indicates the docker-compose version to use.
`NAME:` Specifies the name of the container
`IMAGE:` What image the container uses.
`VERSION:` The version of the specified image, can always use "latest".
`PORT:` To enable network traffic over certain ports use this.
