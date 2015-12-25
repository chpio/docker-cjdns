FROM alpine:3.2

RUN { \
	apk add --update nodejs bash python git build-base linux-headers; \
	git clone https://github.com/cjdelisle/cjdns.git /tmp/cjdns; \
	cd /tmp/cjdns; \
	git checkout 486ec91ed0b5f0df557ad37b8b6898c9e3c5fa05; \
	./do; \
	mv cjdroute /usr/bin; \
	rm /tmp/cjdns -rf; \
	apk del --purge nodejs bash python git build-base linux-headers; \
	rm -rf /var/cache/apk/*; \
}

VOLUME /data/cjdns

ADD start-cjdns /usr/bin/
CMD ["start-cjdns"]
