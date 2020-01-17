FROM php:7.2-fpm-alpine

# Set working directory
WORKDIR /var/www

RUN apk add bash git autoconf gcc icu-dev make g++ zlib-dev libpng-dev libxml2-dev && \
    docker-php-ext-install bcmath gd intl mbstring mysqli pdo pdo_mysql tokenizer xml zip

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy helpers binaries
RUN mkdir /tmp/bin
COPY /bin/* /tmp/bin/
RUN chmod +x /tmp/bin/*
RUN mv /tmp/bin/* /bin/

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["startup"]