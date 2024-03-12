FROM alpine:latest

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN set -ex; \
  apk add --no-cache tzdata curl; \
  curl -L "https://github.com/xtaci/kcptun/releases/download/v${VERSION}/kcptun-${TARGETOS}-${TARGETARCH}-${VERSION}.tar.gz" | tar -xz; \
  mv "client_${TARGETOS}_${TARGETARCH}" /usr/bin/client; \
  mv "server_${TARGETOS}_${TARGETARCH}" /usr/bin/server; \
  chmod +x /usr/bin/client /usr/bin/server; \
  rm -rf /root/*
ENV TZ=Asia/Shanghai
