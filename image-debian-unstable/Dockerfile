FROM debian:jessie

RUN { \
	set -ex; \
	apt-get update; \
	apt-get install -y nodejs git build-essential; \
	git clone https://github.com/hyperboria/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 914519757271a1d4ef2c5d848508497b30fa4005; \
	./do; \
	mv cjdroute /usr/bin; \
	apt-get remove -y nodejs git build-essential; \
	apt-get autoremove -y; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
