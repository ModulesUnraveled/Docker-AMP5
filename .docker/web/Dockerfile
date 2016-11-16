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
    mbstring \
    opcache

# Add custom PHP configuration changes from php.ini
COPY php.ini /usr/local/etc/php/

# Copy and enable our own site configuration -- needed for .htaccess enable.
COPY web.conf /etc/apache2/sites-available/web.conf
RUN a2dissite 000-default && \
    a2ensite web

# Enable mod_rewrite, otherwise Drupal form submission doesn't work.
RUN a2enmod rewrite

RUN rm -rf /var/www/html && \
    ln -s /var/www/drupal/web /var/www/html

# Add site aliases so that Drush can be run from anywhere
COPY aliases.drushrc.php /etc/drush/

# Set the Drush version.
ENV DRUSH_VERSION 8.1.7

# Install Drush 8 with the phar file.
RUN curl -fsSL -o /usr/local/bin/drush "https://github.com/drush-ops/drush/releases/download/$DRUSH_VERSION/drush.phar" && \
  chmod +x /usr/local/bin/drush

# Test your install.
RUN drush core-status
