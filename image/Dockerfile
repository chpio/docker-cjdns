FROM docker.io/buildpack-deps:buster as builder

WORKDIR /build

RUN { set -ex; \
	apt-get update; \
	apt-get install --no-install-recommends -y nodejs; \
}

RUN { set -ex; \
	git clone https://github.com/cjdelisle/cjdns.git cjdns --depth 1 --branch cjdns-v21.2; \
	cd cjdns; \
	git checkout 20ddc268694ea03b940b7294ea04fec75166dcc9; \
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
