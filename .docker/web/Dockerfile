FROM php:5-apache
MAINTAINER brian@fourkitchens.com

RUN apt-get update && apt-get install -yq \
    vim \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libicu-dev

RUN docker-php-ext-install \
    gd \
    json \
    intl \
    pdo \
    pdo_mysql \
    mbstring

RUN rm -rf /var/www/html && \
    ln -s /var/www/drupal/web /var/www/html
