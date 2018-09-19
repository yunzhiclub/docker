# 设置源 
FROM php:5.6-apache
# 使用 apt安装软件
RUN apt-get update && apt-get install -y vim libpng-dev libjpeg-dev libpq-dev \
	&& rm -rf /var/lib/apt/lists/* \
	# 使用docker安装php扩展
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd pdo_mysql \
	&& pecl install -o -f redis \
	&& rm -rf /tmp/pear \
	&& docker-php-ext-enable redis \
	&& chown -R www-data:www-data /var/www/html && a2enmod rewrite\
	# 设置环境变量
	&& sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf \
	&& sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug
RUN echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/php.ini
RUN echo 'xdebug.remote_log=/var/log/xdebug.log' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_autostart=1' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_handler=dbgp' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.profiler_enable=0' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.profiler_output_dir="/var/app/Public"' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_port=9000' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/php.ini
RUN chmod 777 /var/log/
