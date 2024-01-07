FROM php:8.1-fpm-buster

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_MEMORY_LIMIT=-1 \
  TZ=Asia/Tokyo \
  LANG=C.UTF-8

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer

RUN apt-get update && \
  apt-get -y install --no-install-recommends git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath

RUN set -ex \
	&& cd /usr/local/etc \
	sed 's/expose_php = On/expose_php = Off/' /usr/local/etc/php/php.ini-production > /usr/local/etc/php/php.ini

WORKDIR /var/www
