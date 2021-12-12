---
title: "fastapiのリバースプロキシとしてNginxを使う"
date: 2021-12-13T01:05:41+09:00
tags: ["nginx","python","fastapi"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## fastapi設定
fastapiをインストール
```sh
pip install -m fastapi uvicorn
```

## nginxの設定
nginxの設定ファイル`/etc/nginx/nginx.conf`を開き，
以下を追記
uvicornのデフォルトのポートが8000になっているのでserver以下には`localhost:8000`と指定する
```
upstream fastapi{
  server localhost:8000;
}

server {
    listen       80;

    location / {
      proxy_pass http://fastapi;
    }
}
```
設定編集後は再起動
```
systemctl restart nginx
```

## 実行
あとはfastapiを実行して，
[localhostの80番ポート](http://localhost)にアクセスしてfastapi側の処理が実行されていることを確認する．


## reference
[FastAPI + uvicorn + nginxをdocker-composeで構築](https://qiita.com/junkor-1011/items/02ed76b94c60deba8282#web-nginx%E3%81%AB%E3%82%88%E3%82%8Bweb%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC)
