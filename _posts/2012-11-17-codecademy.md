---
layout: post
category : ja
tags : [selfstudy, javascript, codecademy]
title: "Cash Register Part II"
date: 2012-11-17
comments: false
---

ひゃっほう！！Codecademy で [Cash Register Part II](http://www.codecademy.com/courses/cash-register-mark-ii/) おわったぜ！ 

[Recursing on a list](http://www.codecademy.com/courses/cash-register-mark-ii/1#!/exercises/1) で `index + 1` って書くべきところを `index++` って書いてハマってた。まさに[この人と同じ間違い](http://www.codecademy.com/forum_questions/503245c91e5f7e0002043daa)。 

{% highlight perl %}
//bad! This should be inside an object. We'll fix that a bit later
var change = 0; 

function howManyCoins (coinName, coinAmount, coinsSoFar) {
    if (change < coinAmount) {
		console.log(coinsSoFar + " " + coinName);
	} else {
		change -= coinAmount;
		howManyCoins(coinName, coinAmount, coinsSoFar + 1);
	}
}

var currency = [5.00, 1.00, 0.25, 0.10, 0.01];
var coinNames = ["five dollar bills", "one dollar bills", "quarters", "dimes", "pennies"];

function makeChange (coinNames, currency, index) {
	if (index >= currency.length) {
		// and this
		return;
	} else {
		//and this
		howManyCoins(coinNames[index], currency[index], 0);
		// ここの3つめの引数を index++ にして無限ループしてた 
		makeChange(coinNames, currency, index + 1)
	}
}

change = 18.94;
makeChange(coinNames, currency, 0);
{% endhighlight %}

なぜ `++` って書いてたかというと、codecademy の[別のコース](http://www.codecademy.com/courses/javascript-lesson-149/0?curriculum_id=4f4b35445cb288000300000c#!/exercises/1)で出てきて、1減らしたいときここは `--` とも書けるぜ。これちょっと自慢できるぜ。って書いてあったんだよなー。これ。

{% highlight perl %}
function makeRobots(robotsNeeded){
  // Do we need any robots?
  if(robotsNeeded>0){
    // We do?  Well lets make one
    console.log("Robot "+ robotsNeeded+" Created");
    // Removes 1 from robots Needed
    // Also the same as saying robotsNeeded = robotsNeeded -1
    robotsNeeded--;
    // Calls makeRobots with the new number of robots needed
    makeRobots(robotsNeeded);
  }
}
makeRobots(2);
{% endhighlight %}

ここでは、`robotsNeeded = robotsNeeded -1` と `robotsNeeded--` は同じ、という話で、`robotsNeeded -1` と `robotsNeeded--` は同じではないのだけど、そこをカンチガイしていたのだった。

Knowing this will impress your programmer friends, and make you more attractive to people in general. とかいわれたら使ってみたくなるじゃんね！  
よくわかんなくてぶつぶつ言ってたら Twitter で教えてもらった。pre-increment と post-increment ってどう違うの！サイ本の説明よくわかんなかった！  

さださん(@sada_h) の [https://gist.github.com/4088752](https://gist.github.com/4088752) 見て、実行してみて、理解した。

{% highlight perl %}
var i = 1;
// +1 される前の値が出力されるのが i++
console.log(i++) // 1
// そして次に呼び出すときには +1 されている
console.log(i)   // 2

var j = 1;
// +1 された後の値が出力されるのが ++j
console.log(++j) // 2
console.log(j)   // 2
{% endhighlight %}

そうか。index + 1 はOKだし、index = index + 1 でもよくて、++index もよいのだった。index++ がまずかったのね。

残り Build a Blackjack Game, Final だけなんだけど、OOPのとこ復習しないといけないのをひしひしとかんじています。
