FROM php:5.6.40-apache

RUN sed -i 's/deb.debian.org/archive.debian.org/g' /etc/apt/sources.list \
    && sed -i 's/security.debian.org/archive.debian.org/g' /etc/apt/sources.list \
    && sed -i '/stretch-updates/d' /etc/apt/sources.list

RUN apt-get update -y --allow-unauthenticated
RUN apt-get install -y --allow-unauthenticated libjpeg-dev libpng-dev


# 为 php 安装 module
RUN /usr/local/bin/docker-php-ext-configure gd --with-gd \
    --with-webp-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir \
    --enable-gd-native-ttf
RUN /usr/local/bin/docker-php-ext-install mysql mysqli gd zip
# RUN /usr/local/bin/docker-php-ext-enable gd


RUN echo "alias ll='ls -alF'" >> ~/.bashrc
CMD ["apache2-foreground"]