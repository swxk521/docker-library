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
  curl -L "https://codeload.github.com/wangyu-/UDPspeeder/tar.gz/$VERSION" | tar -xzC "/usr/share"; \
  mv "/usr/share/UDPspeeder-$VERSION" "/usr/share/UDPspeeder"; \
  cd "/usr/share/UDPspeeder"; \
  make; \
  strip -s speederv2


FROM alpine:latest
COPY --from=builder /usr/share/UDPspeeder/speederv2 /usr/bin/
RUN chmod +x /usr/bin/speederv2
ENV TZ=Asia/Shanghai
ENTRYPOINT ["/usr/bin/speederv2"]
