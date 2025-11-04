# Use official PHP-FPM base image
FROM php:8.2-fpm

# Install Nginx
RUN apt-get update && apt-get install -y nginx && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /var/www/html

# Copy website files
COPY . /var/www/html

# Configure Nginx
RUN rm /etc/nginx/sites-enabled/default
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Permissions
RUN chown -R www-data:www-data /var/www/html

# Expose port 80
EXPOSE 80

# Start PHP-FPM and Nginx properly
CMD ["sh", "-c", "php-fpm -D && nginx -g 'daemon off;'"]
