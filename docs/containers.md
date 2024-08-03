# Varios contenedores para ser utilizados mediante docker-compose
## Transmission docker-compose Container

```yaml
services:
  transmission:
    image: lscr.io/linuxserver/transmission:latest
    container_name: transmission
    env_file:
      - .env
    volumes:
      - ${TRANSMISSION_CONFIG}:/config
      - ${TRANSMISSION_DOWNLOADS}:/downloads
      - ${TRANSMISSION_WATCH}:/watch
    ports:
      - 9091:9091
      - 51413:51413
      - 51413:51413/udp
    restart: unless-stopped
```

## Archivo .env
```.env
PUID=1000
PGID=1000
TZ=Etc/UTC
TRANSMISSION_WEB_HOME= #optional
USER= #optional
PASS= #optional
WHITELIST= #optional
PEERPORT= #optional
HOST_WHITELIST= #optional
TRANSMISSION_CONFIG=/path/to/transmission/data
TRANSMISSION_DOWNLOADS=/path/to/downloads
TRANSMISSION_WATCH=/path/to/watch/folder
```

## Problema conocido

Es posible que se genere el error:

```sh
transmission    | tail: invalid PID: ‘’
transmission    | jq: parse error: Invalid numeric literal at line 29, column 27
transmission    | [2024-08-03 20:30:20.720] ERR transmission-daemon Error loading config file -- exiting. (/home/buildozer/aports/community/transmission/src/transmission-4.0.6/daemon/daemon.cc:914)
```

Es mi caso se debia a que en el json `settings.json` la key peerport tenia el texto `#optional` pese a haber eliminado este registro del archivo `.env`