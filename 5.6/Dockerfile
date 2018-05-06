#  设置源
FROM php:7.2-apache

# 安装软件及php扩展 参考： https://gist.github.com/chronon/95911d21928cff786e306c23e7d1d3f3
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils openssl libxml2-dev curl vim zip zlib1g-dev \
	&& docker-php-ext-install -j$(nproc) pdo pdo_mysql ctype json mysqli session xml mbstring zip \
	&& a2enmod rewrite

# 安装composer及使用composer安装laravel
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN cd /tmp && curl -sS https://getcomposer.org/installer | php &&  mv composer.phar /usr/local/bin/composer 
# 复制composer.json 防止使用ROOT权限安装报错。安装laravel
COPY ./composer.json /root/.composer/
RUN	composer global require "laravel/installer:" && composer global require "predis/predis:1.*" && export PATH=$PATH:$HOME/.composer/vendor/bin

# 为根文件夹设置owner
RUN chown -R www-data:www-data /var/www/html/

# 定义document_root路径(默认值为/var/www/html)
ENV APACHE_DOCUMENT_ROOT /var/www/html

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf