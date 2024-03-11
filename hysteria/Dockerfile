FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN mkdir /etc/hysteria/ /root/ssl/
COPY config.yaml /etc/hysteria/
COPY server.cer server.key /root/ssl/
RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates curl wget \
	&& curl -L "https://github.com/apernet/hysteria/releases/download/app/v${VERSION}/hysteria-${TARGETOS}-${TARGETARCH}" -o /usr/bin/hysteria \
	&& chmod +x /usr/bin/hysteria

VOLUME /etc/hysteria
VOLUME /root/ssl
ENV TZ=Asia/Shanghai
CMD [ "/usr/bin/hysteria", "server", "-c", "/etc/hysteria/config.yaml" ]
