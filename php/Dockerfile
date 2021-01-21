FROM php:7.0-fpm

# install libraries required by the extensions
RUN apt-get update \
  && apt-get install -y \
    cron \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    libfreetype6-dev

# install extensions
RUN docker-php-ext-configure gd --with-jpeg-dir --with-freetype-dir && \
    docker-php-ext-install \
      bcmath \
      gd \
      intl \
      mbstring \
      mcrypt \
      pdo_mysql \
      soap \
      xsl \
      zip \
      mcrypt

# creating php.ini file
RUN echo 'memory_limit = 2G\n\
max_execution_time = 1800\n\
zlib.output_compression = On' >> /usr/local/etc/php/php.ini

COPY startup.sh /bin/startup.sh
RUN ["chmod", "+x", "/bin/startup.sh"]
WORKDIR /var/www/html

ENTRYPOINT ["sh", "/bin/startup.sh"]
