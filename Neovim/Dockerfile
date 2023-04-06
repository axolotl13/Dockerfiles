FROM alpine:edge

RUN apk update && apk upgrade
RUN apk add --no-cache --virtual build-deps --update \
  git \
  nodejs \
  neovim \
  ripgrep \
  alpine-sdk \
  npm \
  bash \
  gzip \
  xsel \
  wget \
  unzip


RUN addgroup -g 1000 neovim \
  && adduser -D --shell /bin/false -u 1000 -G neovim --home /neovim neovim \
  && chmod 777 -R /neovim \
  && chown neovim:neovim /neovim

WORKDIR /neovim

USER neovim 

