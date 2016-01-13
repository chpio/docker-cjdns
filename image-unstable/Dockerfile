FROM debian:jessie

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \
	git clone https://github.com/hyperboria/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 0aa535b3342bc04191ca002a4dc863b33bc1abea; \
	./do; \
	mv cjdroute /usr/bin; \
	apt-get remove -y $BUILD_DEPS; \
	apt-get autoremove -y; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
