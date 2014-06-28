---
layout: post
title:  "plenv における perlのバージョン切り替え方法"
date:   2014-06-28 23:44:29
categories: perl plenv
---

plenv における perlのバージョン切り替えは下記2パターンが存在します。

1. ディレクトリごとにPerlのバージョンを切り替える(local)

{% highlight zsh %}
# 切り替え
% plenv local 5.18.2
# version 確認
% plenv version
{% endhighlight %}

2. system全体のPerlのバージョンを切り替える(global)

{% highlight zsh %}
# 切り替え
% plenv global 5.18.2
# version 確認
% plenv version
#=>5.18.2 (set by /Users/XXXX/.plenv/version)
{% endhighlight %}


