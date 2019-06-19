# DBのテーブル操作を行うサンプル

画面からSELECT,INSERT,UPDATE,DELETEを行う。

## 準備

$ createdb pandatest
$ psql < dbtest.sql
$ /usr/lib/panda/bin/monsetup -dir directory

## サーバ起動

$ make
$ ./init start

## クライアント起動

$ glclient2

サーバ: http://localhost:8000/rpc/
ユーザ: sample
パスワード: sample
SSL設定: なし

## サーバ終了

$ ./init stop
$ ./init clean
$ make clean
