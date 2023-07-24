FROM alpine:3.18.0

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

ENV TARGETARCH=${TARGETARCH}

WORKDIR /etc/tuic

RUN if [ "$TARGETARCH" = "amd64" ]; then export TARGETARCH="x86_64"; fi \
    && if [ "$TARGETARCH" = "arm64" ]; then export TARGETARCH="aarch64"; fi

RUN wget https://github.com/EAimTY/tuic/releases/download/${VERSION}/${VERSION}-${TARGETARCH}-unknown-${TARGETOS}-musl \
    -O /usr/bin/tuic \
&&  chmod +x /usr/bin/tuic

ENTRYPOINT ["tuic"]
CMD ["-c", "/etc/tuic/config.json"]
