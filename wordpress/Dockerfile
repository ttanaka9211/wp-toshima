FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd zip mysqli pdo_mysql

  RUN chown -R www-user:nginx /var/www/ \
    && chown -R www-user:nginx /var/run/ \
    && chown -R www-user:nginx /var/log/

  RUN useradd -ms /bin/bash -g nginx www-user \
    && echo "www-user:nginx" | chpasswd
USER www-user
