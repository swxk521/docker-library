FROM alpine:edge

ARG VERSION

RUN set -ex; \
  echo "https://dl-cdn.alpinelinux.org/alpine/edge/testing" | tee -a "/etc/apk/repositories"; \
  apk add --no-cache ddclient="${VERSION}"

VOLUME [ "/etc/ddclient" ]

CMD [ "/usr/bin/ddclient", "-foreground" ]
