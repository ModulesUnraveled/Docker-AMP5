FROM php:5-apache
MAINTAINER brian@fourkitchens.com

RUN apt-get update && apt-get install -yq \
    vim

RUN rm -rf /var/www/html && \
    ln -s /var/www/drupal/web /var/www/html
