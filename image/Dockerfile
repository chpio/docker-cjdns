FROM buildpack-deps:stretch as builder

WORKDIR /build

RUN { set -ex; \
	apt-get update; \
	apt-get install --no-install-recommends -y nodejs; \
}

RUN { set -ex; \
	git clone https://github.com/cjdelisle/cjdns.git cjdns --depth 1 --branch cjdns-v20.2; \
	cd cjdns; \
	git checkout 77259a49e5bc7ca7bc6dca5bd423e02be563bdc5; \
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
