# Version: 1.0
FROM php:7.1-apache

# Add a custom virtualhosts file (Just if necessary).
# ADD 000-default.conf /etc/apache2/sites-enabled/

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

# Enable rewrite engine.
RUN a2enmod rewrite
