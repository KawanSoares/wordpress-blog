FROM wordpress:php8.2

RUN apt-get update && \
apt-get install -y \
apt-utils \
libfreetype6-dev \
libjpeg62-turbo-dev \
libmcrypt-dev \
libpng-dev \
libsqlite3-dev \
libcurl4-gnutls-dev
RUN apt-get install git -y
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y libzip-dev
RUN apt-get install -y libonig-dev
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install -j$(nproc) iconv pdo_mysql gd zip curl bcmath opcache mbstring
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-enable iconv pdo_mysql gd zip curl bcmath opcache mbstring
RUN apt-get autoremove -y
RUN apt-get -y install gcc make autoconf libc-dev pkg-config
RUN apt install -y libmagickwand-dev --no-install-recommends
RUN docker-php-ext-enable imagick
RUN echo "extension=imagick.so" > /usr/local/etc/php/conf.d/docker-php-ext-imagick.ini
RUN rm -rf /var/lib/apt/lists/*
EXPOSE 80
WORKDIR /var/www
