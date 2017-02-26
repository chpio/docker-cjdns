FROM debian:jessie

RUN { \
	set -ex; \
	BUILD_DEPS="wget git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \

	# install cjdns
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns --depth 1 --branch cjdns-v19.1; \
	cd /tmp/cjdns; \
	git checkout f4f73cdc120907f9952f7c74abe68394fd2879a0; \
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
