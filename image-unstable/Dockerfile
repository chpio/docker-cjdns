FROM debian:jessie

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \

	# install cjdns
	git clone https://github.com/hyperboria/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 40e87d9419c19063e772e39c7c59a8a8771c5ee8; \
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
