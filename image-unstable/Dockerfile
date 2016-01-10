FROM alpine:3.3

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs bash python git build-base linux-headers"; \
	apk add --update $BUILD_DEPS; \
	git clone https://github.com/hyperboria/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 0aa535b3342bc04191ca002a4dc863b33bc1abea; \
	Seccomp_NO=1 ./do; \
	mv cjdroute /usr/bin; \
	rm /tmp/cjdns -rf; \
	apk del --purge $BUILD_DEPS; \
	rm -rf /var/cache/apk/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
