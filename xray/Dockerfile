FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
COPY config.json /etc/xray/config.json
RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates curl wget unzip \
	&& mkdir -p /var/log/xray /usr/share/xray \
  && curl -L "https://github.com/XTLS/Xray-core/releases/download/v${VERSION}/xray-${TARGETOS}-${TARGETARCH}.zip" -o xray.zip && unzip xray.zip xray && mv xray /usr/bin && rm xray.zip \
  && chmod +x /usr/bin/xray \
	&& wget -O /usr/share/xray/geosite.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat \
	&& wget -O /usr/share/xray/geoip.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat

VOLUME /etc/xray
ENV TZ=Asia/Shanghai
ENTRYPOINT [ "/usr/bin/xray" ]
CMD [ "-config", "/etc/xray/config.json" ]
