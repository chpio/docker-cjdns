FROM debian:jessie

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 13189fde111d0500427a7a0ce06a970753527bca; \
	./do; \
	mv cjdroute /usr/bin; \
	apt-get remove -y $BUILD_DEPS; \
	apt-get autoremove -y; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
