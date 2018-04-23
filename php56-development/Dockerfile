# 设置源 
FROM php:5.6-apache
# 使用 apt安装软件
RUN apt-get update && apt-get install -y vim libpng12-dev libjpeg-dev libpq-dev \
	&& rm -rf /var/lib/apt/lists/* \
	# 使用docker安装php扩展
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd pdo_mysql \
	&& pecl install -o -f redis \
	&& rm -rf /tmp/pear \
	&& docker-php-ext-enable redis \
	# 设置环境变量
	&& sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf \
	&& sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
# 安装xdebug 参考：https://gist.github.com/chadrien/c90927ec2d160ffea9c4
# https://blog.philipphauer.de/debug-php-docker-container-idea-phpstorm/
RUN pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug
RUN echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/php.ini
RUN echo 'xdebug.remote_log=/var/log/xdebug.log' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_autostart=on' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_handler=dbgp' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.profiler_enable=0' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.profiler_output_dir="/var/app/Public"' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_port=9000' >> /usr/local/etc/php/php.ini \
    &&  echo 'xdebug.remote_enable=on' >> /usr/local/etc/php/php.ini