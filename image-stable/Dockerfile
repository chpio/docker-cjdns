FROM alpine:3.3

RUN { \
	apk add --update nodejs bash python git build-base linux-headers; \
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 13189fde111d0500427a7a0ce06a970753527bca; \
	./do; \
	mv cjdroute /usr/bin; \
	rm /tmp/cjdns -rf; \
	apk del --purge nodejs bash python git build-base linux-headers; \
	rm -rf /var/cache/apk/*; \
}

VOLUME /data/cjdns

COPY start-cjdns /usr/bin/
CMD ["start-cjdns"]
