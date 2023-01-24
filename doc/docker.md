# Docker
## 部署
### 命令行
```shell
docker run -d -p 80:80 --name=pixiv xxx
```

### Docker compose
```yaml
version: '3.1'

services:
  pixiv:
    image: xxx
    container_name: pixiv
    restart: always
    environment:
      DISABLE_WEB_JOB: false
    ports:
      - "80:80"
```

## 配置
通过 [环境变量](https://docs.docker.com/compose/compose-file/#environment) 进行配置。所有配置项见 [config.docker.php](../config.docker.php)

> 日志路径：`/var/www/html/storage/logs`

## 任务
### 主动触发更新
```shell
docker exec pixiv php index.php -j=refresh
```
详见 [主动触发更新](./deploy.md)

### 清除日志
```shell
docker exec pixiv php index.php -j=clear-log
```
详见 [清除日志](./deploy.md)