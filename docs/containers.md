# Multiple containers to be used with docker-compose

## Transmission Container

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

### .env File

```.env
PUID=1000
PGID=1000
TZ=Etc/UTC
TRANSMISSION_WEB_HOME= #optional
USER= username
PASS= password
WHITELIST= #optional
PEERPORT= #optional
HOST_WHITELIST= #optional
TRANSMISSION_CONFIG=/path/to/transmission/data
TRANSMISSION_DOWNLOADS=/path/to/transmission/downloads
TRANSMISSION_WATCH=/path/to/transmission/watch
```

### Known Issue

You might encounter the error:

```sh
transmission    | tail: invalid PID: ‘’
transmission    | jq: parse error: Invalid numeric literal at line 29, column 27
transmission    | [2024-08-03 20:30:20.720] ERR transmission-daemon Error loading config file -- exiting. (/home/buildozer/aports/community/transmission/src/transmission-4.0.6/daemon/daemon.cc:914)
```

In my case, it was because the peerport key in the `settings.json` had the text `#optional` even though i had removed this entry from the `.env` file.

## Minidlna Container

```yaml
services:
  minidlna:
    image: vladgh/minidlna
    container_name: minidlna
    restart: unless-stopped
    volumes:
      - <localpath>:/media/video
    network_mode: host
    environment:
      MINIDLNA_MEDIA_DIR_2: /media/video
      MINIDLNA_FRIENDLY_NAME: "RPi DLNA"
```
