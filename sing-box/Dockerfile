FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN mkdir /etc/sing-box/ /root/ssl/
COPY apple.crt apple.key microsoft.crt microsoft.key /root/ssl/
RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates curl wget unzip nftables bash\
	&& mkdir -p /var/log/sing-box /usr/share/sing-box \
        && curl -L "https://github.com/SagerNet/sing-box/releases/download/v${VERSION}/sing-box-${VERSION}-${TARGETOS}-${TARGETARCH}.tar.gz" -o sing-box.tar.gz &&  tar -xzf sing-box.tar.gz \
        && ls -al && mv sing-box*/sing-box /usr/bin && mv sing-box*/*.so /usr/bin && rm sing-box.tar.gz \
        && chmod +x /usr/bin/sing-box
VOLUME /etc/sing-box
VOLUME /root/ssl
ENV TZ=Asia/Shanghai
ENTRYPOINT ["/usr/bin/sing-box"]
