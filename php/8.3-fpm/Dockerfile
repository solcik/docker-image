FROM php:8.3-fpm

ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN install-php-extensions \
		bcmath \
		gd \
		intl \
		opcache \
		pcntl \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		pgsql \
		redis \
		soap \
		sockets \
		zip

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www
