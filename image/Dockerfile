FROM debian:stretch-slim as builder

WORKDIR /build

RUN { set -ex; \
	apt-get update; \
	apt-get install --no-install-recommends -y \
		wget git build-essential python ca-certificates nodejs; \
}

RUN { set -ex; \
	git clone https://github.com/cjdelisle/cjdns.git cjdns --depth 1 --branch cjdns-v20.1; \
	cd cjdns; \
	git checkout bd6b60d817d3126fb45f671c1c7637042a0be937; \
}

RUN { set -ex; \
	cd cjdns; \
	./do; \
}

FROM debian:stretch-slim
COPY start-cjdns /usr/bin/
VOLUME /data/cjdns
CMD ["start-cjdns"]
COPY --from=builder /build/cjdns/cjdroute /usr/bin/
