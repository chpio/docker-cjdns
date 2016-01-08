FROM debian:jessie

RUN { \
	set -ex; \
	apt-get update; \
	apt-get install -y nodejs git build-essential; \
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 13189fde111d0500427a7a0ce06a970753527bca; \
	Seccomp_NO=1 ./do; \
	mv cjdroute /usr/bin; \
	apt-get remove -y nodejs git build-essential; \
	apt-get autoremove -y; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
