# Docker

There's a lot of depth to be found in docker.


To truly utilize docker you want to use docker-compose.
But often the important part is knowing how to specify information, this is where the cheat sheet comes into play.

- [The basic compose](#the-basic-compose)
- [The networked compose](#the-networked-compose)

### The basic compose:
> [!NOTE] 
> Its very basic... 
<details> 
  <summary>Details</summary>

```diff
+ version: ${VERSION}
+ 
+ services:
+  container:
+    container_name: ${NAME}
+    restart: unless-stopped
+    image: ${IMAGE}:${IMAGE_VERSION}
+    ports:
+     - ${PORT}:${PORT}
```
<details> 
  <summary>Variable explanation: </summary>

| Variable | Example | Explanation |
| --------- | ------ | ----------- |
| `VERSION` | 2.8 | This indicates the docker-compose version. |
| `NAME` | container | Specifies the name of the container. |
| `IMAGE` | hello-world | What image the container uses. |
| `IMAGE_VERSION` | latest | The version of the specified image, can always use "latest". |
| `PORT` | 80 | To enable network traffic over certain ports use this. |

</details>
</details>

### The networked compose:
> [!NOTE] 
> Its connected!

<details> 
  <summary>Networked compose: </summary>

```diff
version: ${VERSION}

services:
  container:
    container_name: ${NAME}
    restart: unless-stopped
    image: ${IMAGE}:${VERSION}
    ports:
     - ${PORT}:${PORT}

+    networks:
+      logging-network:
+        ipv4_address: ${IP_ADDRESS}
+        gateway: ${GATEWAY_ADDRESS}
+    dns:
+      - ${DNS}
```
<details> 
  <summary>Variable explanation: </summary>

| Variable | Explanation |
| --------- | ----------- |
| `IP_ADDRESS` | ip-address of the container, remove to use first available. |
| `GATEWAY_ADDRESS` | Gateway of the network, remove to use default. |
| `DNS` | Set a custom DNS server for this specific container. |

</details>
</details>
