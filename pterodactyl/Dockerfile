# ----------------------------------
# Pterodactyl Core Dockerfile
# Environment: glibc + libuuid
# Minimum Panel Version: 0.6.0
# ----------------------------------
FROM frolvlad/alpine-glibc:alpine-3.12

LABEL maintainer='NoxInmortus'

RUN apk add --update --no-cache wget ca-certificates libstdc++ musl libuuid git bash build-base libffi-dev openssl-dev bzip2-dev zlib-dev readline-dev sqlite-dev xz-dev \
  && adduser -D -h /home/container container

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

# Set Python version
ARG PYTHON_VERSION='3.7.6'
# Set pyenv home
ARG PYENV_HOME=$HOME/.pyenv

# Install pyenv, then install python versions
RUN git clone --depth 1 https://github.com/pyenv/pyenv.git $PYENV_HOME && \
    rm -rfv $PYENV_HOME/.git

ENV PATH $PYENV_HOME/bin:$PATH

RUN pyenv install $PYTHON_VERSION
RUN pyenv global $PYTHON_VERSION
RUN pyenv virtualenv 3.7.6 pyplanet-user

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/ash", "/entrypoint.sh"]
