FROM debian:jessie

RUN { \
	set -ex; \
	BUILD_DEPS="nodejs git build-essential python ca-certificates"; \
	apt-get update; \
	apt-get install --no-install-recommends -y $BUILD_DEPS; \

	# install cjdns
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	# cjdns v17.1
	git checkout b2a1d31bfb910f730ff7754d2e478b7d64752dff; \
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
