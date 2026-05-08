FROM alpine:latest

# 声明内置变量，Buildx 会自动填充
ARG TARGETOS
ARG TARGETARCH
ARG VERSION

WORKDIR /root
RUN mkdir -p /etc/tuic/ /root/ssl/
COPY config.toml /etc/tuic/
COPY server.cer server.key /root/ssl/

RUN set -ex \
    && apk add --no-cache tzdata ca-certificates curl wget \
    # 使用临时变量 ARCH 进行转换，避免直接操作 TARGETARCH
    && case "${TARGETARCH}" in \
        "amd64") ARCH="x86_64" ;; \
        "arm64") ARCH="aarch64" ;; \
        *) ARCH="${TARGETARCH}" ;; \
    esac \
    # 在同一个 RUN 指令中使用 $ARCH
    && curl -L "https://github.com/Itsusinn/tuic/releases/download/v${VERSION}/tuic-server-${ARCH}-${TARGETOS}" -o /usr/bin/tuic-server \
    && chmod +x /usr/bin/tuic-server

VOLUME /etc/tuic
VOLUME /root/ssl
ENV TZ=Asia/Shanghai
CMD [ "/usr/bin/tuic-server", "-c", "/etc/tuic/config.toml" ]
