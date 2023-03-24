FROM php:7.4-fpm

COPY composer.lock composer.json /var/www/html/

WORKDIR /var/www/html

ENV DOCKERIZE_VERSION 0.6.1

RUN curl -s -f -L -o /tmp/dockerize.tar.gz https://github.com/jwilder/dockerize/releases/download/v$DOCKERIZE_VERSION/dockerize-linux-armhf-v$DOCKERIZE_VERSION.tar.gz \
      && tar -C /usr/local/bin -xzvf /tmp/dockerize.tar.gz \
      && rm /tmp/dockerize.tar.gz

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash

RUN apt-get update \
      && apt-get install -y --no-install-recommends \
      git \
      vim \
      libmemcached-dev \
      libz-dev \
      libpq-dev \
      libjpeg-dev \
      libpng-dev \
      libfreetype6-dev \
      libssl-dev \
      libmcrypt-dev \
      libzip-dev \
      unzip \
      zip \
      nodejs \
      && docker-php-ext-configure gd \
      && docker-php-ext-configure zip \
      && docker-php-ext-install \
      gd \
      exif \
      opcache \
      pdo_mysql \
      pdo_pgsql \
      pcntl \
      zip \
      && rm -rf /var/lib/apt/lists/*;

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

COPY . /var/www/html

COPY --chown=www:www . /var/www/html

USER www

EXPOSE 9000
CMD ["php-fpm"]
