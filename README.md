# docker cjdns

## Usage

### latest release (libsodium)

```yaml
version: "2"
services:
  cjdns:
    image: chpio/cjdns:sodium
    cap_add:
      - NET_ADMIN
    volumes:
      - ./data-cjdns:/data/cjdns
    devices:
      - /dev/net/tun
```

### latest release (built-in nacl)

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
