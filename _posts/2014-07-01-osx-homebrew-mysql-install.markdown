---
layout: post
title:  "osx に homebrew で mysql を install する"
date:   2014-07-01 02:50:56
categories: osx homebrew mysql install
---

## MySQL のインストール

```
% brew install mysql
```

ここでインストール後の設定方法が出力される。
これらの情報は `brew info mysql` で確認可能。

## データベース及びユーザー設定

* データベースのインストール、格納場所の設定

```
% unset TMPDIR
% mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp
```

* mysql の起動

```
% mysql.server start
```

* password の設定

```
% /usr/local/opt/mysql/bin/mysqladmin -u root password 'new-password'
% /usr/local/opt/mysql/bin/mysqladmin -u root -h YOUR_MACHINE_NAME.local password 'new-password'
```

* mysql データベースの格納場所: /usr/local/var/mysql

## 起動スクリプトの設定

* OS 起動時にmysqlを自動起動するための下記にシンボリックリンクを配備する.

```
% ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
```

* デフォルトではmysqlは落ちても自動で再起動する設定となっているので、サーバ出ない場合はとりあえずこれをオフにしておく.

```
% open ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

^^ 開いたら、 "KeepAlive" の Value を "NO" に設定する.

* スクリプトの有効化
```
% launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
% launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

## note

#### mysqlの再起動

```
% mysql.server stop
% mysql.server start
```

#### my.cnf を使うには

* /etc/my.cnf: global
* /usr/local/var/mysql/my.cnf: server固有
* ~/my.cnf: user固有

```
show variables like "char%";
```
