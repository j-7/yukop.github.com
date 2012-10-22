---
layout: post
category : selfstudy
tags : [progressreport, selfstudy, twitter, geeklatte]
---
## 日報はじめます

趣味プログラミングのようなものの作業記録を残すことにします。学んだことや、つまづいたことや、プロフェッショナルな先輩たちからのお告げなども。  
さかのぼった分もあとで書くかもしれない（こういう場合たいていは書かない）。  
TODO リストを常にどこかに表示しておけるとよいかも。

目的が自分用メモであるうえに、へっぽこなので、たぶんほとんどが、何言ってるかわかんねーぜ！ってことになる気がしている。ゆくゆくは何かの役に立てたらよいけど。

markdown の練習も兼ねてるので、markdown の syntax おさらい。code の中で var 的なもの使いたいけどないのかな。

* [Markdown: Syntax](http://daringfireball.net/projects/markdown/syntax)

### jekyll

2週間くらい触ってなかったらローカルで jekyll を起動する方法からすでに忘れてた。このブログは jekyll と GitHub Pages でできています。

	$ jekyll --server --auto

で [http://localhost:4000/](http://localhost:4000/) で確認。

### Twitter bot
Google App Engine と Python で Twitter bot つくりたい計画。ってことで月齢を一日一回 tweet する bot つくった。
[astral 0.6.2](http://pypi.python.org/pypi/astral/) というぴったりな Package を見つけたのでそれをつかってる。
月齢の数字だけじゃなくて、呼び名がある場合はそれもつぶやくようにした。「わーい、三日月だよー」とかそういうの。

日の出と日没の時間も tweet したいんだ。`sunrise()` とか `sunset()` とかあるからいけるはず。どこかの city を基準にする必要があるのでわたしの都合により Tokyo になっちゃうけど。

16人の Follower のみなさま、できそこないを生暖かく見守ってくれてありがとう。「テストなしでいきなり本番ってすごいよね。いや、いいと思う。」と先輩に呆れられたりした。テスト…ほほう……  
これはテストも含めてエンタテインメントなのです！（キリッ（ごめんなさい

* [@moonphase_bot](https://twitter.com/moonphase_bot)

### Google App Engine

というわけであっぺんじんだけど、これも忘れるのでメモ。Development Web Server の開始。

	dev_appserver.py 俺ぺんじん

デフォルトの port 番号は 8080 で、`dev_appserver.py --port=9999 俺ぺんじん` とかすると port 指定できる。その他 option は[あっぺんじんのドキュメント](https://developers.google.com/appengine/docs/python/tools/devserver?hl=en) みる。

Application の Deploy.

	appcfg.py update 俺ぺんじん

これも詳しくは[あっぺんじんのドキュメント](https://developers.google.com/appengine/docs/python/tools/uploadinganapp?hl=en)みる。


### geeklatte.com
DECONCEPTER 氏からのリクエストで JSONP 吐くようにした。 
Flickr API の場合、

	format=json&nojsoncallback=1

これだと JSON 形式で、

	format=json&jsoncallback=getGeeklatte

これだと callback 関数名指定して JSONP で出力。

* [geeklatte_all.js](http://geeklatte.com/geeklatte_all.js)

### Web Intents
[HTML5 Conference 2012](http://events.html5j.org/conference/2012/09/) についてる WebIntents でシェアボタンをまねっこしてみようとローカルでいろいろ。動くのは確認できたけど置き場所に悩みちゅう。

先日の [#gtuggirls](https://docs.google.com/document/d/1yrznHMMLilPQEQio64EI9Mbqj2SCj_ZiSlRGfisR-K0/edit) ではじめて Web Intents 触った！翌日記念に Web Intents latte つくったら reshare の果てに Paul Kinlan 氏から、言いにくいんだけどロゴ変わったのよね、というコメントをいただき…ってご本人！ワーオ！来週あたらしいロゴでつくります。

* [http://webintents-wiki.appspot.com/](http://webintents-wiki.appspot.com/) （新しいロゴ）

![Today's latte, Web Intents.](http://farm9.staticflickr.com/8046/8098765939_3ffa1b2959_z.jpg)

