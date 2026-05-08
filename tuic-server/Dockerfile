FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN mkdir /etc/tuic/ /root/ssl/
COPY config.toml /etc/tuic/
COPY server.cer server.key /root/ssl/

RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates curl wget \
        && if [ "${TARGETARCH}" = "amd64" ]; then \
	      TUIC_ARCH="x86_64"; \
           elif [ "${TARGETARCH}" = "arm64" ]; then \
	      TUIC_ARCH="aarch64"; \
           fi \
        && curl -L "https://github.com/Itsusinn/tuic/releases/download/v${VERSION}/tuic-server-${TUIC_ARCH}-${TARGETOS}" -o /usr/bin/tuic-server \
        && chmod +x /usr/bin/tuic-server
VOLUME /etc/tuic
VOLUME /root/ssl
ENV TZ=Asia/Shanghai
CMD [ "/usr/bin/tuic-server", "-c", "/etc/tuic/config.toml" ]
