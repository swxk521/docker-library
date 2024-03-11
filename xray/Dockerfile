FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN mkdir /root/xray/ /root/ssl/
COPY config.json /root/xray/
COPY server.cer server.key /root/ssl/
RUN set -ex \
	&& apk add --no-cache tzdata ca-certificates curl wget unzip \
        && if [ "${TARGETARCH}" = "amd64" ]; then \
	      TARGETARCH="64"; \
           elif [ "${TARGETARCH}" = "arm64" ]; then \
	      TARGETARCH="arm64-v8a"; \
           fi \
        && curl -L "https://github.com/XTLS/Xray-core/releases/download/v${VERSION}/xray-${TARGETOS}-${TARGETARCH}.zip" -o xray.zip && unzip xray.zip xray && mv xray /usr/bin && rm xray.zip \
        && chmod +x /usr/bin/xray \
	&& wget -O /usr/share/xray/geosite.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat \
	&& wget -O /usr/share/xray/geoip.dat https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat

VOLUME /root/xray
VOLUME /root/ssl
ENV TZ=Asia/Shanghai
CMD [ "/usr/bin/xray", "-config", "/root/xray/config.json" ]
