FROM php:8.3-fpm

ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN install-php-extensions \
		bcmath \
		gd \
		intl \
		pcntl \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		pgsql \
		redis \
		soap \
		sockets \
		xdebug \
		zip

COPY --from=composer /usr/bin/composer /usr/bin/composer

VOLUME /var/run/php

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www
