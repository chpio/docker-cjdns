# docker cjdns

## Usage

### latest release

```yaml
version: "2"
services:
  cjdns:
    image: chpio/cjdns:latest
    cap_add:
      - NET_ADMIN
    volumes:
      - ./data-cjdns:/data/cjdns
    devices:
      - /dev/net/tun
```

### DIY builds

```sh
$ git clone "https://github.com/chpio/docker-cjdns.git"
$ cd docker-cjdns
$ CJDNS_TAG=cjdns-v20.2 docker-compose up
```
