---
layout: post
category : selfstudy
tags : [progressreport, selfstudy, twitter, geeklatte]
---
## astral and me

### Twitter bot
月齢を淡々とつぶやく Twitter bot [@moonphase_bot](https://twitter.com/moonphase_bot) さんですが、"moon phase calculate python" でぐぐって出てきたやつを使ってみたところ、なんだか計算がずれている。  
でも、いいものをみつけたんだ！Python には astral っていう、sun とか moon とか関連の計算をしてくれる Package があるっぽい。pypi ってところにあったからきっと安心！

まずは覚えたての easy_install でインストールして Expample 通りにやってみる。

	>>> import datetime
	>>> from astral import Astral
	>>> a = Astral()
	>>> a.solar_depression = 'civil'
	>>> city_name = 'Tokyo'
	>>> city = a[city_name]
	>>> print('Information for %s/%s\n' % (city_name, city.country))
	Information for Tokyo/Japan

よしよし。city は Tokyo になってる。

	>>> timezone = city.timezone
	>>> print('Timezone: %s' % timezone)
	Timezone: Asia/Tokyo

Timezone おっけー。

	>>> print('Latitude: %.02f; Longitude: %.02f\n' % \
	... (city.latitude, city.longitude))
	Latitude: 35.68; Longitude: 139.68

Latitude おっけー。

	>>> sun = city.sun(date=datetime.datetime.now(), local=True)
	>>> print('Dawn:    %s' % str(sun['dawn']))
	Dawn:    2012-10-17 05:23:38+09:00

Tokyo の Sun の Dawn 把握！

でも moon_phase() のつかいかたがわからない。ちゃんと本家のドキュメント読んだよ！英語のやつ！でも書いてないんだよーー！ここで先輩からのお告げ。  
「ソースコード読め」

ソースコードね…ほほう……読みます…失礼しました。

	$ sudo easy_install astral

ッターン！で悦に入っている場合ではなかった。ダウンロードしてきたものをまるごとつっこんでおく場所を作るといいよ。へえー…cool...    
あらためて [http://pypi.python.org/pypi/astral/](http://pypi.python.org/pypi/astral/) みると、ちゃんとここに Download っていうすごくわかりやすいボタンがあるじゃあないかッ！

	>>> import datetime
	>>> from astral import *
	>>> city_name = 'Tokyo'
	>>> a = Astral()
	>>> city = a[city_name]
	>>> print city
	Tokyo/Japan, tz=Asia/Tokyo, lat=35.68, lon=139.68
	>>> print city.moon_phase(datetime.datetime.now())
	24

うーむ。それらしい数字はでてきたけど、おとといくらいが新月だったはずだから 24 のはずないんだよなあ…。おかしい。

	>>> print city.moon_phase()
	24

これでも

	>>> print city.moon_phase(None)
	24

これでも結果は同じ。うーむ。再びソースコードみる。

`class City(object):` の下にある `def moon_phase(self, date=None):` 

`class Astral(object):` の下にある `def moon_phase(self, date, tz):`

なんかふたつあったのね。で、

	>>> print a.moon_phase()
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	TypeError: moon_phase() takes exactly 3 arguments (1 given)

引数 は 3 つ必要なのね（このうち 1 こは self っていうの慣れないけどまあ置いとく）。

	>>> print a.moon_phase(None, None)
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	  File "/Library/Python/2.7/site-packages/astral-0.6.2-py2.7.egg/astral.py", line 1732, in moon_phase
	    jd = self._julianday(date, tz)
	  File "/Library/Python/2.7/site-packages/astral-0.6.2-py2.7.egg/astral.py", line 1763, in _julianday
	    day = date.day
	AttributeError: 'NoneType' object has no attribute 'day'

こっちの引数 date は city のとはちがうのか。

	>>> print a.moon_phase(datetime.datetime.now(), None)
	3

うお！3 でた！三日月でたーーーー！わーーーー！めでたい！

city.moon_phase がなんでうまくいかないのかよくわからないけどそういうこともあるらしい。

