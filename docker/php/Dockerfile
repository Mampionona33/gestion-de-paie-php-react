FROM php:8.2-apache

WORKDIR /var/www/app

# Install PHP 8.2 and required extensions
RUN apt-get update && apt-get install -y \
    php8.2 \
    php8.2-mysql \
    php8.2-mbstring \
    php8.2-xml \
    php8.2-gd \
    php8.2-curl \
    php8.2-zip \
    && rm -rf /var/lib/apt/lists/*

# Install Composer
COPY --from=composer:2.5.4 /usr/bin/composer /usr/bin/composer

# Enable mod_rewrite
RUN a2enmod rewrite

# Install PDO
RUN docker-php-ext-install pdo_mysql

# Expose port 80
EXPOSE 80

CMD ["apache2-foreground"]
