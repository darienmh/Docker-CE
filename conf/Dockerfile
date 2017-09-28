FROM php:5-fpm

LABEL maintainer="darienmh@gmail.com"

#ADD wkhtmltopdf /usr/bin/wkhtmltopdf

RUN php -m \
#&& chmod +x /usr/bin/wkhtmltopdf \
&& apt-get update \
&& apt-get install -y --force-yes --no-install-recommends \
	libssl-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpq-dev \
	libzip-dev \
	libxslt-dev \
	libmcrypt-dev \
	libicu-dev \
#	libxrender1 \
#    libfontconfig1 \
#	libx11-6 \
#	libxext6 \
	imagemagick \
	
&& pecl install xdebug \
&& docker-php-ext-enable xdebug \
&& pecl install imagick \
&& docker-php-ext-enable imagick \

&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \

&& docker-php-ext-install -j$(nproc) \
	pgsql \
	pdo_pgsql \
	soap \
	gd \
	bcmath \
	xsl \
	zip \
	intl \
	mcrypt \

&& php -m \
&& apt-get autoremove -y \
&& apt-get clean all \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
