---
layout: post
category : selfstudy
tags : [selfstudy, python, sakura]
title: "setuptools がインストールできないよメモ (1)"
date: 2013-01-15
comments: false
---
さくらの VPS で Jinja2 使いたい。のでインストールしようと思ったんだけど、そういえば setuptools も pip もまだ入れてなかったよー。
以下の手順で試してみたんだけど、うまくいかないよメモ。

## 1. Python 2.7.3 インストール
[ドットインストール &gt; さくらのVPSの基礎 &gt; #20 ソースからPythonを入れてみよう](http://dotinstall.com/lessons/basic_sakura_vps/8020)

	$ cd /tmp
	$ wget http://python.org/ftp/python/2.7.3/Python-2.7.3.tgz	
	$ tar xvzf Python-2.7.3.tgz	
	$ ./con	igure
	$ make
	$ sudo make install

Python はもともと 2.6.6 が入ってたんだけど、さくらのVPS の設定をドットインストールみながらやった勢いで、2.7.3 を入れた。

## 2. setuptools のインストール

[「さくらのVPS」に setuptools （Python) をインストール](http://azmax51.wordpress.com/2011/09/27/%E3%80%8C%E3%81%95%E3%81%8F%E3%82%89%E3%81%AEvps%E3%80%8D%E3%81%AB-setuptools-%EF%BC%88python-%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/)

	$ cd /usr/local/src/
	$ wget http://pypi.python.org/packages/2.7/s/setuptools/setuptools-0.6c11-py2.7.egg
	省略...
	$ chmod +x setuptools-0.6c11-py2.7.egg
	$ ./setuptools-0.6c11-py2.7.egg --prefix=/usr/local

Permission denied っていわれたので、最後の行、 sudo でもう一度やってみたら、エラーメッセージは以下のとおり。

	./setuptools-0.6c11-py2.7.egg: line 3: exec: python2.7: not found

setuptools-0.6c11-py2.7.egg の中身みてみた。if なんとか then exec python2.7 -c なんとか、って書いてある。
	
	$ python2.7

でも python 起動できてるんだけど、なぜ？　ってとこで行き詰まり中。



