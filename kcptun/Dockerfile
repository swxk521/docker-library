FROM alpine:edge

ARG TARGETOS
ARG TARGETARCH
ARG VERSION

RUN set -ex; \
  apk add --no-cache curl; \
  mkdir -p "/usr/share/kcptun"; \
  curl -L "https://github.com/xtaci/kcptun/releases/download/v${VERSION}/kcptun-${TARGETOS}-${TARGETARCH}-${VERSION}.tar.gz" | \
    tar -xzC "/usr/share/kcptun"; \
  mv "/usr/share/kcptun/client_${TARGETOS}_${TARGETARCH}" "/usr/share/kcptun/client"; \
  mv "/usr/share/kcptun/server_${TARGETOS}_${TARGETARCH}" "/usr/share/kcptun/server"


FROM scratch

COPY --from=0 /usr/share/kcptun/client /usr/share/kcptun/server /bin/
