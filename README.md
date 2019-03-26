## DNMP

通过Docker一键部署LNMP，请确保已经安装docker和docker-compose。

包含以下内容：

- `nginx:alpine`:
  - 说明
    - 已支持`TLS 1.3`
  - 网站目录: `./nginx/html`
  - 虚拟主机配置目录: `./nginx/conf.d`
- `mysql:5`
  - 数据库目录: `./mysql`
- `php:7-fpm-alpine`:
  - 说明:
    - 基于初始镜像额外安装了`pdo_mysql`、`mysqli`、`gd`插件。
    - 若想安装其他插件，请自行修改`Dockerfile`。
  - `php.ini`目录: `./php-fpm`
- `acme.sh`:
  - 说明:
    - 用于申请ssl证书。
  - 证书存储目录: `./ssl`
  - 使用方法: 参考[官方文档](https://github.com/Neilpang/acme.sh)

### 开始

1. 将项目clone到本地
2. 在`docker-compose.yml`文件中更改你需要的端口和数据库密码。
3. 执行`docker-compose up -d`，并等待启动完成。

### 命令

Nginx:

- 检查`Nginx`配置:
  - `docker exec nginx nginx -t`
- `Nginx`重载配置:
  - `docker exec nginx nginx -s reload`

php:

- 安装插件(以pdo_mysql为例):
  - `docker exec php docker-php-ext-install pdo_mysql`
  - 最好修改`Dockerfile`实现，否则无法保留

### 常用Nginx配置

- 启用`php`:
  - `include enable-php.conf`
- 启用带`pathinfo`的`php`:
  - `include enable-php-pathinfo.conf`
- 启用`HSTS`:
  - `add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" always;`
  - 此句可根据需要适当调整
