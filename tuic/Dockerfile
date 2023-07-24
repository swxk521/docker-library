FROM alpine:3.18.0

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /etc/tuic

RUN if [ "$TARGETARCH" = "amd64" ]; then \
    wget https://github.com/EAimTY/tuic/releases/download/${VERSION}/${VERSION}-x86_64-unknown-${TARGETOS}-musl \
    -O /usr/bin/tuic \
    && chmod +x /usr/bin/tuic; fi

RUN if [ "$TARGETARCH" = "arm64" ]; then \
    wget https://github.com/EAimTY/tuic/releases/download/${VERSION}/${VERSION}-aarch64-unknown-${TARGETOS}-musl \
    -O /usr/bin/tuic \
    && chmod +x /usr/bin/tuic; fi

COPY config.json /etc/tuic/

ENTRYPOINT ["tuic"]
CMD ["-c", "/etc/tuic/config.json"]
