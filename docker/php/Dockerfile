ARG composer_version
ARG php_version

FROM composer:${composer_version} as vendor

FROM php:${php_version}-fpm

COPY --from=vendor /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y \
    git \
    libxml2-dev \
    libonig-dev \
    libpq-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    zlib1g-dev \
    libzip-dev \
    unzip \
    libbz2-dev \
    libldap2-dev \
    libxslt-dev \
	&& docker-php-ext-install -j$(nproc) gd \
	&& docker-php-ext-install bcmath \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install pdo_pgsql \
	&& docker-php-ext-install soap \
    && docker-php-ext-install intl \
    && docker-php-ext-install zip \
    && docker-php-ext-install bz2 \
    && docker-php-ext-install calendar \
    && docker-php-ext-install dba \
    && docker-php-ext-install exif \
    && docker-php-ext-install gettext \
    && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu \
    && docker-php-ext-install ldap \
    && docker-php-ext-install sockets \
    && docker-php-ext-install xmlrpc \
    && docker-php-ext-install xsl \
    && mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

ARG user

RUN mkdir /home/${user} \
    && chown 1000:1000 /home/${user}

WORKDIR /var/www/html/

USER 1000:1000