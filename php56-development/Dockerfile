# 设置源 
FROM registry.cn-beijing.aliyuncs.com/mengyunzhi/thinkphp:latest

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
    &&  echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/php.ini