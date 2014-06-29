---
layout: post
title:  "plenv の 導入からperlのインストール、切り替え、cpanm導入まで"
date:   2014-06-28 23:56:56
categories: perl plenv carton
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

