# ----------------------------------
# Pterodactyl Core Dockerfile
# Environment: glibc + libuuid
# Minimum Panel Version: 0.6.0
# ----------------------------------
FROM frolvlad/alpine-glibc:alpine-3.12

LABEL maintainer='NoxInmortus'

RUN apk add --update --no-cache wget ca-certificates libstdc++ musl libuuid libffi-dev python3-dev openssl-dev zlib zlib-dev gcc bzip2 bzip2-dev xz-dev xz sqlite sqlite-dev \
  && adduser -D -h /home/container container

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]
