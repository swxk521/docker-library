FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN set -ex \
  && apk add --no-cache tzdata curl \
  && curl -L "https://github.com/fatedier/frp/releases/download/v${VERSION}/frp_${VERSION}_${TARGETOS}_${TARGETARCH}.tar.gz" | tar -xz \
  && cd "frp_${VERSION}_${TARGETOS}_${TARGETARCH}" && mv frpc /usr/bin/client && mv frps /usr/bin/server \
  && mkdir /etc/frp && mv frpc.toml /etc/frp/ && mv frps.toml /etc/frp/ \
  && chmod +x /usr/bin/client /usr/bin/server \
  && rm -rf /root/*
VOLUME /etc/frp
ENV TZ=Asia/Shanghai
