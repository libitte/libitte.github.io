---
layout: post
title:  "plenv における perlのバージョン切り替え方法とcpanmの導入"
date:   2014-06-28 23:44:29
categories: perl plenv
---

plenv における perlのバージョン切り替えは下記2パターンが存在します。

#### ディレクトリごとにPerlのバージョンを切り替える(local)

```
# 切り替え
% plenv local 5.18.2
# version 確認
% plenv version
```

#### system全体のPerlのバージョンを切り替える(global)

```
# 切り替え
% plenv global 5.18.2
# version 確認
% plenv version
#=>5.18.2 (set by /Users/XXXX/.plenv/version)
```

現在のperlにcpanmをインストールする方法は下記のとおりです。

```
% plenv install-cpanm
```

