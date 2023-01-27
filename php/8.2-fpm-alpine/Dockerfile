FROM php:8.2-fpm-alpine

RUN apk update \
	&& apk add --no-cache --allow-untrusted --repository http://dl-cdn.alpinelinux.org/alpine/edge/community/ \
		autoconf \
		curl \
		g++ \
		git \
		gnu-libiconv \
		icu-dev \
		libpng-dev \
		libtool \
		libzip-dev \
		make \
		postgresql-dev \
		unzip \
		zip

ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php

RUN pecl install mongodb \
	&& pecl install ds \
	&& pecl install redis \
	&& docker-php-ext-enable \
		ds \
		redis \
	&& docker-php-ext-install \
		bcmath \
		gd \
		intl \
		opcache \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		pgsql \
		zip \
	&& curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
	&& composer self-update --stable

RUN apk del \
		autoconf \
		g++ \
		libtool \
		make \
	&& rm -rf /var/cache/apk/* \
	&& rm -rf /tmp/*

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

WORKDIR /usr/local/app
