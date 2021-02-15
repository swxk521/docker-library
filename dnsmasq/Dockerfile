FROM alpine:edge

ARG VERSION

RUN set -ex; \
  apk add --no-cache dnsmasq="${VERSION}"

EXPOSE 53
EXPOSE 53/udp
EXPOSE 67/udp

VOLUME [ "/etc/dnsmasq.d" ]

CMD [ "/usr/sbin/dnsmasq", "-k", "-q" ]
