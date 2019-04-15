# Version: 1.0
FROM php:7.1-apache

# Install some dependencies.
RUN apt update && \
    apt install -y curl git wget nano
RUN apt-get update && \
    apt-get install -y libmagickwand-dev --no-install-recommends && \
    pecl install imagick && \
    docker-php-ext-enable imagick
RUN apt-get update && \
    apt-get install -y zlib1g-dev libmcrypt-dev

# Install all PHP extensions.
RUN docker-php-ext-install mysqli 
RUN docker-php-ext-install bcmath 
RUN docker-php-ext-install pdo_mysql 
RUN docker-php-ext-install mcrypt 
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install zip
RUN docker-php-ext-install soap
RUN apt-get update && apt-get install -y libwebp-dev libxpm-dev && \
    docker-php-ext-configure gd --with-gd --with-webp-dir --with-jpeg-dir \
    --with-png-dir --with-zlib-dir --with-xpm-dir --with-freetype-dir \
    --enable-gd-native-ttf
RUN docker-php-ext-install gd
RUN apt-get update && \
    apt-get install -y libxslt-dev && \
    docker-php-ext-install xsl
RUN docker-php-ext-install intl

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '48e3236262b34d30969dca3c37281b3b4bbe3221bda826ac6a9a62d6444cdb0dcd0615698a5cbe587c3f0fe57a54d8f5') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

# Add a custom virtualhosts file (Just if necessary).
ADD 000-default.conf /etc/apache2/sites-enabled/

# Enable rewrite engine.
RUN a2enmod rewrite
