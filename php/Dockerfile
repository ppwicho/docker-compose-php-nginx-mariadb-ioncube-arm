FROM php:7.4-fpm  
ENV PHP_VERSION=7.4
ENV IONCUBE_VERSION=7.4
ENV PHP_CONFD_PATH=/usr/local/etc/php/conf.d/
# Maybe there is a better way to detect the system architecture, I'm ussing M1 ARM here 
ENV LOADER=aarch64 

RUN apt-get update  && apt-get install --no-install-recommends -y \
    unzip \ 
    zlib1g \ 
    libpng-dev \
    cron

RUN docker-php-ext-install \ 
    pdo \
    pdo_mysql \
    gd

RUN mkdir -p /usr/local/lib && \ 
    curl -sSlL  -o /tmp/ioncube.tar.gz https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_${LOADER}.tar.gz \  
    && tar -x --strip-components=1 -C /usr/local/lib -f /tmp/ioncube.tar.gz ioncube/ioncube_loader_lin_${IONCUBE_VERSION}.so

RUN (echo "zend_extension = /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so" > ${PHP_CONFD_PATH}/ioncube.ini)
RUN chown root.root /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so
RUN chmod 751 /usr/local/lib/ioncube_loader_lin_${IONCUBE_VERSION}.so

