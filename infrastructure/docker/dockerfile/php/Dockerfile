FROM php:8.1-fpm
RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    libpq-dev
RUN docker-php-ext-install pdo \
        pgsql pdo_pgsql
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug
RUN echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host = host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_port = 9005" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.extended_info = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN curl -sS https://getcomposer.org/installer | php --  --install-dir=/usr/bin --filename=composer
