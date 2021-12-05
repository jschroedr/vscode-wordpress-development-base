FROM wordpress:latest

# install xdebug and enable it as an extension
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# install development binaries
RUN apt-get update && apt-get install git -y

# install composer
RUN apt install wget unzip -y
RUN wget -O composer-setup.php https://getcomposer.org/installer && php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# set the xdebug mode
# allow xdebug to initialize when one of the accepted triggers are set
#
# see docs:
# https://xdebug.org/docs/step_debug
# https://xdebug.org/docs/all_settings#start_with_request
# https://xdebug.org/docs/step_debug#xdebug_connect_to_client
#
# typically, the most reliable way to use xdebug with phpunit is to invoke
# xdebug_connect_to_client() within your bootstrap.php file
RUN echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.start_with_request=trigger" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# ensure the pdo mysql driver is installed and enabled
RUN docker-php-ext-install pdo_mysql
RUN sed -i "s/;extension=pdo_mysql/extension=pdo_mysql/" /usr/local/etc/php/php.ini-production
RUN sed -i "s/;extension=pdo_mysql/extension=pdo_mysql/" /usr/local/etc/php/php.ini-development