FROM php:7.4-fpm-alpine

RUN apk update \
	&& apk add --no-cache --allow-untrusted --repository http://dl-cdn.alpinelinux.org/alpine/edge/community/ \
		autoconf \
		curl \
		freetds \
		g++ \
		git \
		gnu-libiconv \
		icu-dev \
		libpng-dev \
		libtool \
		libzip-dev \
		make \
		postgresql-dev \
		unixodbc-dev \
		unzip \
		zip

ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

RUN pecl install ds \
	&& pecl install mongodb \
	&& pecl install redis \
	&& pecl install xdebug \
	&& pecl install sqlsrv \
	&& pecl install pdo_sqlsrv \
	&& docker-php-ext-enable \
		ds \
		redis \
		xdebug \
		sqlsrv \
		pdo_sqlsrv \
	&& docker-php-ext-install \
		bcmath \
		gd \
		intl \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		pgsql \
		zip \
	&& curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
	&& composer self-update --snapshot

RUN apk del \
		autoconf \
		g++ \
		libtool \
		make \
	&& rm -rf /var/cache/apk/* \
	&& rm -rf /tmp/*

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /usr/local/app
