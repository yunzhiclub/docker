# docker 地址
registry.cn-beijing.aliyuncs.com/mengyunzhi/thinkphp:3.2-development
操作系统:debian jessie

# 官方源
本image使用的为php官方源，版本为5.6-apache。官方地址为：[https://hub.docker.com/_/php/](php docker官方链接)

# 变量
`{APACHE_DOCUMENT_ROOT}`  apache文档根目录。
其它变量设置请参数官方文档

# 端口
80, 443

# xdebug使用方法
* 将本地项目文件夹映射到docker文件夹。
* 在phpStorm中新建PHP Web Page
* 新建servers。端口设置为apacher的映射端口
* Host: localhost Port:8088 Debugger: xdebug
* 选择Use path mappings
* 设置本机的文件夹与docker文件夹的对应路径
* 浏览器安装xdebug插件

# 参考项目
[https://github.com/yunzhiclub/paper_approving](https://github.com/yunzhiclub/paper_approving)
