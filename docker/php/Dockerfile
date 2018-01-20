FROM php:7.1-fpm
RUN apt-get update
RUN apt-get install -y g++
RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y libjpeg62-turbo-dev
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y libpng-dev
RUN apt-get install -y libpq-dev
RUN pecl install redis
RUN docker-php-ext-enable redis
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-install -j$(nproc) mcrypt
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd
# RUN docker-php-ext-configure mysql -with-mysql=/usr/local/mysql
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install json
RUN docker-php-ext-install zip
COPY --from=composer:1.5 /usr/bin/composer /usr/bin/composer
EXPOSE 9000
