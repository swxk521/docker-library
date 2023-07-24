FROM alpine:3.18.0

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /etc/tuic

RUN wget https://github.com/EAimTY/tuic/releases/download/${VERSION}/${VERSION}-${TARGETARCH}-unknown-${TARGETOS}-musl \
    -O /usr/bin/tuic \
&&  chmod +x /usr/bin/tuic

ENTRYPOINT ["tuic"]
CMD ["-c", "/etc/tuic/config.json"]
