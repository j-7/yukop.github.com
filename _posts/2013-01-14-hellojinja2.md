---
layout: post
category : selfstudy
tags : [selfstudy, python]
title: "Hello Jinja2"
date: 2013-01-14
comments: false
---
雪が降ったのでおうちでもくもくしてた。

[geeklatte.com](http://geeklatte.com) プロジェクトの Phase 2 で 1 写真 1 URL にしたいなーと思ってるので、今日はまずいまある index.html を Jinja2 でテンプレート化した。

とりあえずローカルで動くところまでできたので忘れないように自分用メモ。

{% highlight perl %}
env = Environment(loader = FileSystemLoader('../templates'))
template = env.get_template('index.html')
{% endhighlight %}

../templates/index.html (実行するファイルからのパス) をテンプレートとして使ってて、

{% highlight perl %}
output = template.render(photos=photos, photoset=photoset)
save_html = open('../public_html/index.html', 'w')
save_html.write(output.encode('utf-8'))
{% endhighlight %}

生成した文字列を output って変数に入れてそれを ../public_html/index.html に書き出してる。
`photos=photos, photoset=photoset` はテンプレートで使う変数の中身が何なのか教えてる。

サーバでテストしたかったんだけど、さくらのVPSに setuptools か pip 入れようとしたらあるものがないとか言われて結局どこかからあるはずの何かが見えてないことになってるみたいなので、明日 Python2.7.3 インストールしなおしてみる。

[https://github.com/yukop/geeklatte/commit/5132dd47d3a16befdab321e257a277a1973666f5](https://github.com/yukop/geeklatte/commit/5132dd47d3a16befdab321e257a277a1973666f5)
