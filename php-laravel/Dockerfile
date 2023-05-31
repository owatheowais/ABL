# Use a base image with PHP and the desired version
# FROM php:8.0-apache
FROM systemsdk/docker-apache-php-laravel

# Set the working directory in the container
WORKDIR /var/www/html

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql zip

# Enable Apache Rewrite module
RUN a2enmod rewrite

# Copy the Laravel application files to the container
COPY . .

# Set the appropriate file permissions
RUN chown -R www-data:www-data \
    /var/www/html/storage \
    /var/www/html/bootstrap/cache

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install application dependencies
RUN composer install --optimize-autoloader --no-dev

# Set the Apache document root
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -i -e 's|/var/www/html|${APACHE_DOCUMENT_ROOT}|g' /etc/apache2/sites-available/000-default.conf

# Expose port 80 for web traffic
EXPOSE 80

# Start the Apache server
CMD ["apache2-foreground"]
