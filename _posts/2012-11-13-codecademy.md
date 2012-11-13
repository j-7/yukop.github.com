---
layout: post
category : selfstudy
tags : [selfstudy, javascript, codecademy]
---
## Project: Recursive Functions 

Codecademy で [Project: Recursive Functions](http://www.codecademy.com/courses/javascript-lesson-149/0) が終わった。
コンピュータに5枚の手札を配って、その中に特定のカードがあるかどうか当てるゲーム。ここまでは順調！

	var cards = new Array("ace","king","queen","jack",10,9,8,7,6,5,4,3,2);
	var hand = [];

	function dealHand(numberOfCards){
		//if numberOfCards is greater than zero
		if(numberOfCards > 0){
			// Store a random number
			var n = Math.floor(Math.random() * cards.length);
			// Add card to the hand array
			hand.push(cards[n]);
			// Output the card
			console.log("Your card is " + cards[n]);
			// remove card selected from cards array
			cards.splice([n],1);
			// remove from numberOfCards
			numberOfCards--;
			// recursive function call 
			dealHand(numberOfCards);
		}	
	}

	function goFish(num, guess){
		// if num is greater than zero
		if(num >= 0){
			if(hand[num]===guess){
				console.log("A Match for", hand[num]);
				return;
			} else if (num === 0){
				console.log("Go Fish: No matches for " + guess);
			}
			// remove from num
			num--;
		  // recursive function call... remember to use both arguments
		  goFish(num, guess);
		}
	}
	// Call dealHand and goFish
	dealHand(5);
	goFish(cards.length, 3);


[昨日の日報ポストのコメント欄](https://plus.google.com/u/0/106825171914368756519/posts/QA9w1buSh7F)より。  
recursion と tail recursion と stack overflow の関係について聞いて、  
[Stack Overflow](http://stackoverflow.com/) って洒落てんなー！  
Google の検索結果["再帰"](https://www.google.co.jp/search?q=%E5%86%8D%E5%B8%B0), ["recursion"](https://www.google.com/search?q=recursion﻿)も洒落てんなー！  
って思ったよ。