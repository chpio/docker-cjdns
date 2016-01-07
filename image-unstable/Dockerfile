FROM alpine:3.3

RUN { \
	set -ex; \
	apk add --update nodejs bash python git build-base linux-headers; \
	git clone https://github.com/hyperboria/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 914519757271a1d4ef2c5d848508497b30fa4005; \
	Seccomp_NO=1 ./do; \
	mv cjdroute /usr/bin; \
	rm /tmp/cjdns -rf; \
	apk del --purge nodejs bash python git build-base linux-headers; \
	rm -rf /var/cache/apk/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
