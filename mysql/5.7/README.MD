# 示例
```yml
# 版本号
version: '3'

networks:
  hostnet:
    driver: bridge
    ipam:
      driver: default
      config:
        - subnet: 172.16.238.0/24

# 定义服务
services:
  hhwl.mysql:
    container_name: hhwl.mysql
    image: registry.cn-beijing.aliyuncs.com/mengyunzhi/mysql:5.7
    networks:
      hostnet:
        ipv4_address: 172.16.238.15
    expose:
      - "3306"
    volumes:
      - "./custom.cnf:/etc/mysql/conf.d/custom.cnf"
    ports:
      - "3307:3306"
    environment:
      - MYSQL_USER=root
      - MYSQL_PASSWORD=
      - MYSQL_ALLOW_EMPTY_PASSWORD=true
      - MYSQL_DATABASE=databasename
```


custom.cnf用于配置数据库的默认编码，防止乱码产生
```
[mysqld]
character-set-server = utf8
collation-server = utf8_unicode_ci
skip-character-set-client-handshake
```
