FROM alpine:3.3

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs bash python git build-base linux-headers"; \
	apk add --update $BUILD_DEPS; \
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout b2a1d31bfb910f730ff7754d2e478b7d64752dff; \
	Seccomp_NO=1 ./do; \
	mv cjdroute /usr/bin; \
	rm /tmp/cjdns -rf; \
	apk del --purge $BUILD_DEPS; \
	rm -rf /var/cache/apk/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
