# Docker

There's a lot of depth to be found in docker.


To truly utilize docker you want to use docker-compose.
But often the important part is knowing how to specify information, this is where the cheat sheet comes into play.

> [!CAUTION]
> To keep oversight i recommand to use an number to identify containers like: `001-NAME`.

- [Basic compose](#Basic-compose)
- [Networked compose](#Networked-compose)
- [Local volume compose](#Local-volume-compose)
- [Docker volume compose](#Docker-volume-compose)
- [Network volume compose](#Network-volume-compose)

---

### Basic compose:
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
</details>
<details> 
  <summary>Variables </summary>

| Variable | Example | Explanation |
| --------- | ------ | ----------- |
| `VERSION` | 2.8 | This indicates the docker-compose version. |
| `NAME` | container | Specifies the name of the container. |
| `IMAGE` | hello-world | What image the container uses. |
| `IMAGE_VERSION` | latest | The version of the specified image, can always use "latest". |
| `PORT` | 80 | To enable network traffic over certain ports use this. |

</details>

---

### Logged compose:
> [!NOTE] 
> Its sending logs now 
<details> 
  <summary>Details</summary>

```diff
version: ${VERSION}
 
services:
  container:
    container_name: ${NAME}
    restart: unless-stopped
    image: ${IMAGE}:${IMAGE_VERSION}
    ports:
     - ${PORT}:${PORT}
+    logging:
+      driver: syslog
+      options:
+        syslog-address: "udp://${LOG_HOST}:${LOG_PORT}"
+        tag: ${NAME}
```
</details>
<details> 
  <summary>Variables </summary>

| Variable | Example | Explanation |
| --------- | ------ | ----------- |
| `LOG_HOST` | IP-ADDRESS | The ip-address of the syslog server. |
| `LOG_PORT` | 5514 | Port on which the applciation will send logs. |

</details>

---

### Networked compose:
> [!NOTE] 
> Its connected!

<details> 
  <summary>Details </summary>

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
</details>
<details> 
  <summary>Variables </summary>

| Variable | Explanation |
| --------- | ----------- |
| `IP_ADDRESS` | ip-address of the container, remove to use first available. |
| `GATEWAY_ADDRESS` | Gateway of the network, remove to use default. |
| `DNS` | Set a custom DNS server for this specific container. |

</details>
