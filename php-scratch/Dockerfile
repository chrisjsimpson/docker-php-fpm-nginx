FROM php:7.3-cli
RUN apt-get update \
    && apt-get install -y curl zlib1g-dev libzip-dev unzip

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"\
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

# Install php zip extension
RUN docker-php-ext-install zip
# Install laravel cli
RUN composer global require laravel/installer

# Add laravel cli to PATH
ENV PATH /root/.composer/vendor/bin/:$PATH

# Wait container
CMD ["tail", "-f", "/dev/null"]
