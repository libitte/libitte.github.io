---
layout: post
title:  "plenv の 導入と perl のインストール方法"
date:   2014-06-28 23:56:56
categories: perl plenv
---

#### plenv のインストール(zshの場合)

```
% git clone git://github.com/tokuhirom/plenv.git ~/.plenv
% git clone git://github.com/tokuhirom/Perl-Build.git ~/.plenv/plugins/perl-build/
% echo 'export PATH="$HOME/.plenv/bin:$PATH"' >> ~/.zshrc
% echo 'eval "$(plenv init -)"' >> ~/.zshrc
% exec $SHELL -l
```


#### perl のインストール

```
# インストール可能なperlのバージョン一覧
% plenv install -l #たくさん出るのでless or grep 推奨
# インストール
% plenv install 5.18.2
# global で5.18.2のperlを適用
% plenv global 5.18.2
# 現在のperlのバージョンを確認
% plenv version
```
