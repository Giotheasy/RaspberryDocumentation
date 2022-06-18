# Configuration via Docker with docker-compose

```yaml
version: "2.1"
services:
  transmission:
  image: lscr.io/linuxserver/transmission
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Europe/London
  volumes:
    - /path/to/data:/config
    - ./downloads:/downloads
    - /path/to/watch/folder:/watch
  ports:
    - 9091:9091
    - 51413:51413
    - 51413:51413/udp
  restart: unless-stopped
```
