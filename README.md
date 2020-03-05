# Sandbox DB

MySQLの挙動をサクッと確認するために必要な環境を整えるためのもの

## Introduction

このリポジトリは、 https://github.com/datacharmer/test_db をサンプルデータとした
MySQLの挙動確認を手軽に行えることを目指すものです。

## Installation

### Clone

seeds はサブモジュールなので、cloneするときに以下のオプションをつけてcloneしてください。じゃないと、ファイルが足りないと出ると思います。

```bash
$ git clone --recursive git@github.com:datacharmer/test_db.git
```

やばい！すでにcloneしちゃった！という方は、以下でもいけます。

```bash
$ git submodule init
$ git submodule update
```

### Build and run

```bash
$ docker-compose up
```

:warning: 初回起動時はdumpをリストアするのに時間が掛かるため、気長に待つ。以下が表示されているときはリストア中なので待つ。

```bash
sandbox_db | /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/1_employees.sh
sandbox_db | mysql: [Warning] Using a password on the command line interface can be insecure.
```

が表示されれば、完了している

```bash
sandbox_db | 2020-03-05T03:53:28.534767Z 0 [Note] mysqld: ready for connections.
sandbox_db | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
```

## How to access to database's

`localhost:30360` に対して 接続してください。ユーザ名は `root` 、パスワードは `password` でいけます。

## 滅びの呪文

以下のコマンドを叩き、再び `docker-compose run` をすれば、何事もなかったことになる

```bash
$ docker-compose down --volumes
```