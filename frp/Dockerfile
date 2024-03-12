FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN set -ex \
  && apk add --no-cache tzdata curl \
  && curl -L "https://github.com/fatedier/frp/releases/download/v${VERSION}/frp_${VERSION}_${TARGETOS}_${TARGETARCH}.tar.gz" | tar -xz \
  && cd "frp_${VERSION}_${TARGETOS}_${TARGETARCH}" && mv frpc /usr/bin/ && mv frps /usr/bin/ \
  && mkdir /etc/frp && mv frpc.toml /etc/frp/ && mv frps.toml /etc/frp/ \
  && chmod +x /usr/bin/frps /usr/bin/frpc \
  && rm -rf /root/*
VOLUME /etc/frp
ENV TZ=Asia/Shanghai
