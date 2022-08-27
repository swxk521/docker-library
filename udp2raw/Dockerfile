FROM debian

RUN set -ex; \
  apt update; \
  apt upgrade -y; \
  apt install -y \
    build-essential \
    git \
  ; \
  mkdir -p "/usr/share"; \
  git clone "https://github.com/wangyu-/udp2raw.git" "/usr/share/udp2raw"; \
  cd "/usr/share/udp2raw"; \
  make; \
  strip -s udp2raw


FROM alpine

COPY --from=0 /usr/share/udp2raw/udp2raw /bin/

RUN set -ex; \
  apk add --no-cache \
    iptables \
    ip6tables \
  ;

ENTRYPOINT ["/bin/udp2raw"]
