FROM alpine:edge
MAINTAINER Daniel Guerra
RUN apk add --update --nocache lighttpd
CMD ["/usr/sbin/lighttpd-angel","-D","-f","/etc/lighttpd/lighttpd.conf"]
