```bash

# 環境構築
$ vagrant up
$ vagrant ssh

# dbaccessのサンプル
$ cd panda-sample2
$ cd dbaccess
$ make
$ sudo -u postgres createuser -d $USER
$ sudo service jma-receipt stop
$ createdb pandatest
$ psql pandatest < dbtest.sql
$ /usr/lib/panda/bin/monsetup -dir directory
$ ./init start

# Macローカルのmonsiajから接続
サーバ：http://localhost:28000/rpc/
ユーザ：sample
パスワード：sample

```

-----

以下、元のREADME

# panda-sample2

日医標準レセプトソフトのオンプレ版のミドルウェアmontsuqiのサンプルプログラム

## 動作条件

OS: Ubuntu 18.04
ミドルウェア: panda-3.0.0以上

## 環境構築

1. 日レセ5.1をインストールする
    * インストールマニュアル
    * https://www.orca.med.or.jp/receipt/download/bionic/bionic_install_51.html
