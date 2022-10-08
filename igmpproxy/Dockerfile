FROM alpine:edge

ARG VERSION

RUN set -ex; \
  apk add --no-cache igmpproxy="${VERSION}"

ENTRYPOINT [ "/usr/sbin/igmpproxy", "-n" ]
