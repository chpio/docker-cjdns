FROM docker.io/buildpack-deps:buster as builder

WORKDIR /build

RUN { set -ex; \
	apt-get update; \
	apt-get install --no-install-recommends -y nodejs; \
}

RUN { set -ex; \
	git clone https://github.com/cjdelisle/cjdns.git cjdns --depth 1 --branch cjdns-v20.6; \
	cd cjdns; \
	git checkout a6dcc71ab50b1944b46373de3b337edcd5829d81; \
}

RUN { set -ex; \
	cd cjdns; \
	./do; \
}

FROM docker.io/debian:buster-slim
COPY start-cjdns /usr/bin/
VOLUME /data/cjdns
CMD ["start-cjdns"]
COPY --from=builder /build/cjdns/cjdroute /usr/bin/
