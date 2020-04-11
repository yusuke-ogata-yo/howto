# イメージファイル関連操作
## 一覧表示
```bash
docker image ls
```
## イメージファイル削除
```bash
docker image rm [image_name|hash]
```

# コンテナの制御
## コンテナの実行
```bash
docker container run [image_name|hash]
```
## コンテナの停止
```bash
docker container stop [image_name|hash]
```

## 実行中コンテナの一覧
```bash
docker container ls -a
```

## 実行済みコンテナの一括削除
```bash
docker container prune
```

# イメージファイルの更改
## タグ名を付ける
- [user_name]/[tag_name]:[version]
  - yusukeogata/test:v1.0.0
```bash
docker tag [src_tag_name] yusukeogata/text:v1.0.0
```
## docker hub にログイン
```bash
docker login
```
- この後、ユーザ名(yusukeogata)とpw(1M)を入力

## イメージファイルのアップロード
```bash
docker push [tag_name]
```

# docker-entrypoint.sh の書き方
```bash
#! /bin/sh

env

exec "$@"
```
# Dockerfile の書き方
```bash
FROM centos:7

COPY docer-entrypoint.sh /var/tmp

RUN mv /var/tmp/docker-entrypoint.sh /usr/local/bin; \
    chmod +x /user/local/bin/docker-entprypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]
CMD["echo", "Hello World"]
```