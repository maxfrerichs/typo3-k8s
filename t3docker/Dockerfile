FROM composer:2 as build

COPY composer* /build/

WORKDIR /build
RUN composer install --ignore-platform-reqs --optimize-autoloader

FROM php:8.2-apache
ENV APACHE_DOCUMENT_ROOT /var/www/html/public/
RUN apt-get update && apt-get install -y \
		libfreetype-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd
COPY --from=build /build/public /var/www/html/public
COPY --from=build /build/vendor /var/www/html/vendor
RUN chown -R www-data:www-data /var/www

COPY docker-entrypoint.sh /usr/local/bin/

ENTRYPOINT ["docker-entrypoint.sh"]
CMD "apache-foregroun"
USER www-data
