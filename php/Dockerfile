FROM  php:7.2-fpm
#RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
#RUN  apt-get clean
RUN  apt-get update 
RUN apt-get install -y --no-install-recommends \
        curl \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg-dev \
        libpng-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
        libicu-dev \
        libzip-dev \
        libbz2-dev \
        libmemcached-dev
RUN docker-php-ext-configure gd --with-jpeg-dir=/usr/lib --with-freetype-dir=/usr/include/freetype2 && docker-php-ext-install gd
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install bz2
RUN docker-php-ext-install calendar


RUN pecl install zip && docker-php-ext-enable zip
RUN pecl install redis && docker-php-ext-enable redis
RUN pecl install mongodb && docker-php-ext-enable mongodb
RUN pecl install memcached && docker-php-ext-enable memcached
RUN pecl install yaf && docker-php-ext-enable yaf

RUN echo "yaf.use_namespace = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-yaf.ini
RUN echo "yaf.use_spl_autoload = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-yaf.ini

RUN echo "安装完毕！"