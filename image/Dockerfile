FROM debian:stretch-slim

RUN { \
	set -ex; \
	BUILD_DEPS="wget git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \

	# install cjdns
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns --depth 1 --branch cjdns-v20.1; \
	cd /tmp/cjdns; \
	git checkout bd6b60d817d3126fb45f671c1c7637042a0be937; \
	./do; \
	mv cjdroute /usr/bin; \

	# clean up
	apt-get remove -y $BUILD_DEPS; \
	apt-get autoremove -y; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
