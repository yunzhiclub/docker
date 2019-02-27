# docker 地址
registry.cn-beijing.aliyuncs.com/mengyunzhi/thinkphp:3.2-development
操作系统:debian jessie

# 官方源
本image使用的为php官方源，版本为5.6-apache。官方地址为：[php docker官方链接](https://hub.docker.com/_/php/)

# 变量
`{APACHE_DOCUMENT_ROOT}`  apache文档根目录。
其它变量设置请参数官方文档

# 端口
80, 443

# xdebug使用方法
* 新建CLI Interpreter -> new -> docker -> PHP executable: /usr/local/bin/php
* 新建Servers, 将本地项目文件夹映射到`docker`对应文件夹。选择Use path mappings，设置本机的文件夹与docker文件夹的对应路径
* 新建项目配置信息 -> PHP Remote Debug，配置上面新建的service，以及IDE KEY: PHPSTORM
* 浏览器安装xdebug插件

# 参考项目
[https://github.com/yunzhiclub/paper_approving](https://github.com/yunzhiclub/paper_approving)
