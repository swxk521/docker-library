FROM alpine:edge

ARG VERSION

COPY rootfs/ /

RUN set -ex; \
  apk add --no-cache \
    iptables \
    ip6tables \
    openvpn="${VERSION}" \
  ;

EXPOSE 1194
EXPOSE 1194/udp

VOLUME [ "/etc/openvpn" ]

ENTRYPOINT [ "/sbin/init" ]
