FROM php:8.0-fpm-bullseye

RUN apt-get update \
	&& apt-get install -y \
		git \
		libcurl4-openssl-dev \
		libfreetype6-dev \
		libicu-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
		libpq-dev \
		libssl-dev \
		libxml2-dev \
		libwebp-dev \
		libzip-dev \
		pkg-config \
		unzip \
		zip \
	&& pecl install ds \
	&& pecl install mongodb \
	&& pecl install redis \
	&& pecl install xdebug \
	&& docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
	&& docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp \
	&& docker-php-ext-enable \
		ds \
		mongodb \
		redis \
		xdebug \
	&& docker-php-ext-install \
		bcmath \
		gd \
		intl \
		pcntl \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		pgsql \
		soap \
		sockets \
		zip \
	&& curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
	&& composer self-update --stable \
	&& apt-get clean -y \
	&& apt-get autoclean -y \
	&& apt-get autoremove -y \
	&& rm -rf /var/lib/apt/lists/* /var/lib/log/* /tmp/* /var/tmp/*

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www
