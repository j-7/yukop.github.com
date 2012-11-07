---
layout: post
category : selfstudy
tags : [selfstudy, codecademy, javascript, progressreport]
---
## More Fun with Arrays 終わった

先週、日報書けるような活動ができなかったので、リハビリのため Codecademy.  
JavaScript Fundamentals の [More Fun with Arrays](http://www.codecademy.com/courses/working-with-indexed-associate-and-multi-dimensional-arrays) がおわったー。  
これであと残りは 1コースと4演習。本日の、へー、と思ったことをメモしておきます。  

* splice 使った [Array.splice](https://developer.mozilla.org/ja/docs/JavaScript/Reference/Global_Objects/Array/splice)
* push も使った [Array.push](https://developer.mozilla.org/ja/docs/JavaScript/Reference/Global_Objects/Array/push)
* `object[array[i]]` みたいに書けるのかー。なるほど。
* 入れ子 loop して、`array[i][j][k]` みたいに書けるのかー。そりゃそうか。
* `array[i].key` みたいに書けるのかー。そりゃそうか。
* for in loop でなぜか var 忘れがち。たぶんまだ書き慣れてないんだわ。
* Array の名前に複数形の s つけるんだけど、あとから参照するときに s の有無で間違えてるの気づかずにハマったりした。初心者乙。
* 同じコース内で quotation がシングルだったりダブルだったりっていうどうでもいいところが気になる。

Section 5 の Putting It All Together、最終的にはこんなん。トランプのカードを作って Robert と Joe に 5枚ずつ配った。

	//here's our players array from exercise 1
	var players = [];
	players[0] = {'name': 'Robert', hand: []};
	players[1] = {'name': 'Joe', hand: []};

	//here's our code to create the deck
	var suits = ['clubs','diamonds','hearts','spades'];
	var ranks = [2,3,4,5,6,7,8,9,10,'J','Q','K','A'];
	var deck = [];
	for (var i = 0; i < suits.length; i++) {
	    for (var j = 0; j < ranks.length; j++) {
	        var card = {'rank': ranks[j], 'suit':suits[i]};
	        deck.push(card);
	    }
	}

	//This will shuffle the deck. Nothing for you to do here. Just here to 
	//make the final output a little more realistic
	deck.sort(function() {return 0.5 - Math.random()});

	//Deal 5 cards to each player. Make sure you deal them out 
	//one player at a time, just like in a real poker game.
	var c = 0
	for (var i = 0; i < 5; i++) {
		for (var p = 0; p < players.length; p++) {
			var card = deck[c];
			players[p].hand.push(card);
			c++;
		}
	}