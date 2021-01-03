# ----------------------------------
# Pterodactyl Core Dockerfile
# Environment: glibc + libuuid
# Minimum Panel Version: 0.6.0
# ----------------------------------
FROM frolvlad/alpine-glibc:alpine-3.12

LABEL maintainer='NoxInmortus'

RUN apk add --update --no-cache wget curl ca-certificates libstdc++ musl libuuid git bash build-base libffi-dev openssl-dev bzip2-dev zlib-dev readline-dev sqlite-dev xz-dev \
  && adduser -D -h /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

ENV PYENV_ROOT=$HOME/.pyenv
ENV PATH=$PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH

#RUN git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT && \
#  rm -rfv $PYENV_ROOT/.git
#RUN git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
#RUN eval "$(pyenv init -)"
#RUN eval "$(pyenv virtualenv-init -)"

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]
