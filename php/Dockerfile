FROM php:8.1-fpm  
ENV PHP_VERSION=8.1
ENV IONCUBE_VERSION=8.1
ENV PHP_CONFD_PATH=/usr/local/etc/php/conf.d/
# Maybe there is a better way to detect the system architecture, I'm ussing M1 ARM here 
ENV LOADER=aarch64 

RUN apt-get update  && apt-get install --no-install-recommends -y \
    unzip \ 
    zlib1g \ 
    libpng-dev \
    cron \
    nano \
    tzdata

RUN docker-php-ext-install \ 
    pdo \
    pdo_mysql \
    gd
#Set Time Zone in PHP 
ENV TZ="America/Mexico_City"
# Ioncube Installing
RUN mkdir -p /usr/local/lib && \ 
    curl -sSlL  -o /tmp/ioncube.tar.gz https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_${LOADER}.tar.gz \  
    && tar -x --strip-components=1 -C /usr/local/lib -f /tmp/ioncube.tar.gz ioncube/ioncube_loader_lin_${IONCUBE_VERSION}.so
RUN (echo "zend_extension = /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so" > ${PHP_CONFD_PATH}/0-ioncube.ini)
RUN chown root.root /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so
RUN chmod 751 /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so
# XDEBUG Installing
RUN pecl install xdebug
RUN (echo "zend_extension = $(find /usr/local/lib/php/extensions -name 'xdebug.so')"\
     > ${PHP_CONFD_PATH}/8-ext-xdebug.ini)
COPY ./php/xdebug.ini ${PHP_CONFD_PATH}/9-ext-xdebug.ini
# cronjobs 
COPY ./php/crontab.conf /etc/cron.d/whmcs_cron