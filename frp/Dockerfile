FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN set -ex \
  && apk add --no-cache tzdata curl \
  && curl -L "https://github.com/fatedier/frp/releases/download/v${VERSION}/frp_${VERSION}_${TARGETOS}_${TARGETARCH}.tar.gz" | tar -xz \
  && cd "frp_${VERSION}_${TARGETOS}_${TARGETARCH}" && mv frpc /usr/bin/ && mv frps /usr/bin/ \
  && chmod +x /usr/bin/frps /usr/bin/frpc \
  && rm -rf /root/*
ENV TZ=Asia/Shanghai
