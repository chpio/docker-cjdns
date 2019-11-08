FROM buildpack-deps:buster as builder

WORKDIR /build

RUN { set -ex; \
	apt-get update; \
	apt-get install --no-install-recommends -y nodejs; \
}

RUN { set -ex; \
	git clone https://github.com/cjdelisle/cjdns.git cjdns --depth 1 --branch cjdns-v20.4; \
	cd cjdns; \
	git checkout 45cdd8b3eebb18b6239feeef3b787e40d773edfb; \
}

RUN { set -ex; \
	cd cjdns; \
	./do; \
}

FROM debian:buster-slim
COPY start-cjdns /usr/bin/
VOLUME /data/cjdns
CMD ["start-cjdns"]
COPY --from=builder /build/cjdns/cjdroute /usr/bin/
