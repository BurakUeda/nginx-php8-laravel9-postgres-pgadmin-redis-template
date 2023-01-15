FROM php:8.2-fpm-alpine
WORKDIR /var/www/html

RUN apk add --no-cache --virtual buildDeps autoconf \
		$PHPIZE_DEPS \
		nodejs \
		npm \
		oniguruma-dev \
		curl \
		libtool \
		libxml2-dev \
		libmcrypt-dev \
		libpq-dev \
		freetype-dev \
		libjpeg-turbo-dev \
		libpng-dev \
		icu \
		make \
		zlib-dev \
		icu-dev \
		g++ \
		imagemagick \
		imagemagick-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install mbstring \
		pdo \
		pdo_pgsql \
		pgsql \
		bcmath \
		opcache \
		xml \
		-j$(nproc) gd \
		intl \
	&& pecl install redis \
		imagick \
	&& docker-php-ext-enable pdo_pgsql \
		redis \
		imagick \
		intl

#Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer 

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

#Laravel
RUN composer global require "laravel/installer"