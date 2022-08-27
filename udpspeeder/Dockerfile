FROM debian

RUN set -ex; \
  apt update; \
  apt upgrade -y; \
  apt install -y \
    build-essential \
    git \
  ; \
  mkdir -p "/usr/share"; \
  git clone "https://github.com/wangyu-/UDPspeeder.git" "/usr/share/UDPspeeder"; \
  cd "/usr/share/UDPspeeder"; \
  make; \
  strip -s speederv2


FROM scratch

COPY --from=0 /usr/share/UDPspeeder/speederv2 /bin/

ENTRYPOINT ["/bin/speederv2"]
