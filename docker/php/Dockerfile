FROM php:8.2
ENV REDISDB=redis
ENV DYNAMODB=dynamo
ENV SCYLLA=scylla
ENV COMPOSER_ALLOW_SUPERUSER=1

RUN apt update && apt upgrade -y
WORKDIR /app

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \ 
    php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \ 
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" 

RUN mv /app/composer.phar /usr/local/bin/composer

# RUN /usr/local/bin/composer require aws/aws-sdk-php

RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

RUN apt install -y awscli git unzip inetutils-ping python3-cassandra

RUN pecl install redis
RUN echo "extension=redis.so">>/usr/local/etc/php/php.ini



    

