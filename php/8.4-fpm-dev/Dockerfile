FROM php:8.4-fpm

ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN apt-get update \
	&& apt-get install -y \
		unzip \
		zip \
	&& install-php-extensions \
		apcu \
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
		zip \
	&& apt-get clean -y \
	&& apt-get autoclean -y \
	&& apt-get autoremove -y \
	&& rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

COPY --from=composer /usr/bin/composer /usr/bin/composer

VOLUME /var/run/php

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www
