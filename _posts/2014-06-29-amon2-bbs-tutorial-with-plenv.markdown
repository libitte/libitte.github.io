---
layout: post
title:  "plenv 管理 perl で amon2 の bbs tutorial"
date:   2014-06-29 14:54:56
categories: perl plenv carton amon2 tutorial
---

#### skelton の作成

```
% plenv exec amon2-setup.pl BBS
% cd BBS
% plenv exec carton install
```

#### database のセットアップ (とりあえずsqliteを用いる)

* sql/sqlite.sql に下記のテーブル定義を追加

```
% head -n 60 sql/sqlite.sql |tail -n 9                                                               (git)-[master]
CREATE TABLE IF NOT EXISTS sessions (
    id           CHAR(72) PRIMARY KEY,
    session_data TEXT
);

CREATE TABLE IF NOT EXISTS entry (
    entry_id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    body     varchar(255) NOT NULL
);
```

* スキーマの適用

```
% sqlite3 db/development.db < sql/sqlite.sql
```

#### Teng にスキーマ追加

* lib/BBS/DB/Schema.pm のテーブル定義を [Amon2 BBS Tutorial][bbs_tutorial] にしたがって書き換える。

#### controller の実装

* lib/BBS/Web/Dispatcher.pm を [Amon2 BBS Tutorial][bbs_tutorial] に従って書き換える。

#### template の編集

* tmpl/index.tx を [Amon2 BBS Tutorial][bbs_tutorial] に従って書き換える。

#### TESTの実行

```
% plenv exec carton exec prove
```

#### web server 起動

```
% plenv exec carton exec perl -Ilib script/bbs-server
```

#### 動作確認

[http://0:5000/][http://0:5000/]

[bbs_tutorial]: http://amon.64p.org/bbs_tutorial.html
[http://0:5000/]: http://0:5000/
