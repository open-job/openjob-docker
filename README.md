# Openjob

## Docker

build
```shell
cd build && docker build --tag=openjob:1.0.6 .
```

.env
```properties
OJ_DS_URL=jdbc:mysql://127.0.0.1:3306/openjob?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
OJ_LOG_STORAGE_MYSQL_URL=jdbc:mysql://127.0.0.1:3306/openjob?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
```
 
start
```shell
docker run --env-file .env -it -d -p 8080:8080 626f74431178 /bin/bash
```

## docker-compose

docker-compose.yml
```yaml
version: '3'
services:
  openjob-server:
    image: openjob/openjob-server:latest
    restart: always
    container_name: openjob-server
    environment:
      - OJ_DS_URL=jdbc:mysql://127.0.0.1:3306/openjob?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
      - OJ_LOG_STORAGE_MYSQL_URL=jdbc:mysql://127.0.0.1:3306/openjob?useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
    ports:
      - "8080:8080"
```

start
```shell
docker-compose up
# or
docker-compose up -d

```

## docker hub
```
docker login

docker tag openjob:1.0.6 openjob/openjob-server:1.0.6

docker push openjob/openjob-server:1.0.6
```
