## DNMP

通过Docker一键部署LNMP，请确保已经安装docker和docker-compose。

包含以下内容：

- `nginx:alpine`: 已支持`TLS 1.3`
  - 网站目录: `./nginx/html`
  - 虚拟主机配置: `./nginx/conf.d`
- `mysql:5`
  - 数据库目录: `./mysql`
- `php:7-fpm-alpine`: 另外安装了`pdo_mysql`、`zip`、`mysqli gd`插件。
  - `php.ini`目录: `./php-fpm`
- `acme.sh`: 用于申请ssl证书。
  - 证书存储目录: `./ssl

### 开始

1. 将项目clone到本地
2. 在`docker-compose.yml`文件中更改你需要的端口和数据库密码。
3. 执行`docker-compose up -d`，并等待启动完成。

### 命令

Nginx:

- 检查`Nginx`配置: `docker exec nginx nginx -t`
- `Nginx`重载配置: `docker exec nginx nginx -s reload`
