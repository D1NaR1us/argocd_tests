FROM nginx
RUN apt-get update && apt-get install -y \
    php \
    php-fpm
COPY index.html /usr/share/nginx/html