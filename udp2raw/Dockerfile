FROM debian AS builder

ARG VERSION

RUN set -ex; \
  apt update; \
  apt upgrade -y; \
  apt install -y \
    build-essential \
    git \
    curl \
  ; \
  mkdir -p "/usr/share"; \
  curl -L "https://codeload.github.com/wangyu-/udp2raw/tar.gz/$VERSION" | tar -xzC "/usr/share"; \
  mv "/usr/share/udp2raw-$VERSION" "/usr/share/udp2raw"; \
  cd "/usr/share/udp2raw"; \
  make; \
  strip -s udp2raw


FROM alpine:3.18
COPY --from=builder /usr/share/udp2raw/udp2raw /usr/bin/
RUN apk add --no-cache tzdata iptables ip6tables && chmod +x /usr/bin/udp2raw
ENV TZ=Asia/Shanghai
ENTRYPOINT ["/usr/bin/udp2raw"]
