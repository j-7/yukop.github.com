---
layout: post
category : ja
tags : [selfstudy, python, gaeja, twitter]
title: "@geeklatte_botが病気だった"
date: 2012-12-08
comments: false
---

わたしのかわいい第二子 [@geeklatte_bot](https://twitter.com/geeklatte_bot) が、ローカルで実行するとちゃんとつぶやくんだけど、毎日15時05分になっても何も言わないので、 cron.yaml が間違ってるのかなと思ってた。

まあ待て。原因ここかもって言う前に、うまくいってなかったらどこ見るの？log見れ！logってどこですか先輩！あ、わかった、あれか！ダッシュボードみたいなやつ！というわけでここ見るべきでした。 

* [https://appengine.google.com/](https://appengine.google.com/) 

ここの、該当する Application の Main の Logs ってとこ。  

import json でエラーが出て No module named json て言われてた！
App Engine には json てモジュールは入ってないのね。ローカルにはインストールしてたので、ローカルで実行してうまくいってたから気づかなかったのだった。
App Engine にはほとんど標準モジュールしか入ってないと思って気をつけたほうがよさそうね。

ぐぐったら Stack Overflow に解決策のってた。  

* [How can I parse JSON in Google App Engine?](http://stackoverflow.com/questions/1171584/how-can-i-parse-json-in-google-app-engine) 

`from django.utils import simplejson as json` 

これかー。Django 0.96 は Google App Engine に最初から入っていて、その中の simplejson ていうモジュールを、json. で使えるようにしてるってことだよね、と理解した。

これで、[@geeklatte_bot](https://twitter.com/geeklatte_bot)  さんも元気に動き出しました。よかった。