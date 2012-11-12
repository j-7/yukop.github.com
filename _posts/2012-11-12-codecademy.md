---
layout: post
category : selfstudy
tags : [selfstudy, javascript, codecademy]
---
## Recursion in JavaScript 

Codecademy で [Recursion in JavaScript](http://www.codecademy.com/courses/javascript-lesson-205) が終わった！手ごわかった！

このコースの前に、[Review of Object-Oriented Programming](http://www.codecademy.com/courses/intro-to-object-oriented-programming) っていうコースがあり、それにくっついてる演習が [Project: Cash Register Part II](http://www.codecademy.com/courses/cash-register-mark-ii) で、その中にこんなのがでてきたのです。

	var change = 0;
	function howManyQuarters(howMuchMoney) {
	    //fill this in
	    if (howMuchMoney < 0.25){
	    	change = howMuchMoney;
	    	return 0;
	   	} else {
	   		return 1 + howManyQuarters(howMuchMoney - 0.25);
	   	}
	}
	change = 0.99;
	console.log ("Pay out " + howManyQuarters(change) + " quarters");
	console.log ("And you'll have " + change * 100 + " pennies left over"); 

なにこれ。なんで howManyQuarters がぐるぐるしてるのかさっぱりわかんない！  
（後から考えるとそもそも `howManyQuarters(howMuchMoney - 0.25)` これが function に見えてなかった）

と嫌になりかけてたところ、ん、Section のタイトルに Recursing on a number ってあるよね。で次のコース、Recursion in JavaScript だよね。そっち先にやったらよさそうだよね。

Recursion やったるで！Section 1 では function と loop のおさらい。Section 2 でこれ。  

	function factorial(n) {
	  // Termination condition to prevent infinite recursion
	  if (n < 0) {
	    console.log("Can't make a factorial from a negative number.");
	    return;
	  }
	  // Base case
	  if (n === 0) {
	    return 1;
	  }
	  // What's wrong with this picture? Why won't this recursion work?
	  return n * factorial(n - 1);
	}

	factorial(5);

Base case と Termination condition が何のためにあるのかはわかったけど、  
`return n * factorial(n - 1);` これ……わからん… `factorial(n)` の中なのに `factorial(n - 1)` って？ううう。

すみません先輩わかりませんたすけてください。

図解するとこういうことだった。Recursion はマトリョーシカだった。

![Recursion visualization](http://farm9.staticflickr.com/8484/8178924670_db9ab69d2c_z.jpg)

もしくは、階段を降りていっていちばん下で何か拾い、またいちばん上まで戻ってきたら何かが完成してた！とか。   

> It is a visual guide to how values are stored in the stack.

	1.factorial(3) {
		return 3 * factorial(2);
	2.	factorial(2) {
			return 2 * factorial(1);
	3.		factorial(1) {
				return 1 * factorial(0);
	4.			factorial(0) {
	A=				return 1;
				};
	5.		factorial(1) {
	B=      		return 1; // 1 * 1
	     	};
	6.	factorial(2) {
	C=		return 2; // 2 * 1
	   };
	7.factorial(3) {
	D=	return 6; // 3 * 2
	};

その説明は以下。

> You may be wondering where the computer is storing the values returned by each function call in our recursion. That is a very good question, and it has an answer!
> 
> When you run a program, the data that is produced within that program (variables, function calls, etc.) are stored in the stack, which you can think of as a temporary storage device for the computer.
> 
> Every time a function is called within a program, the returned value of that function is stored in the stack.

data が stack に store されるの...うん... よくわからないので Hint を見る。

> This is boring, I know. Let's get out of here. It gets better. Just press Run.

OK, got it! Run.

次にわかんなくなったのはここ。int から順番にカウントダウンしていったのを stack という array に入れといて、それをひとつずつ掛ける function.

	var stack = [];

	function countDown(int) {
	  stack.push(int);
	  if (int === 1) {	
	    return 1;
	  }
	    return countDown(int - 1);
	}
	// [7, 6, 5, 4, 3, 2, 1]

	// ここまでは大丈夫。

	function multiplyEach() {
	  // Remove the last value of the stack 
	  // and assign it to the variable int
	  int = stack.pop();
	  x = stack.length;
	  // Base case
	  if (x === 0) {
	    return int;
	  }

	  // ここまでも大丈夫。でも以下の Recursive case に何書けばいいのかわかんなかった。

	  // Recursive case
	  else {
		return int * multiplyEach();
	  }
	}

	// Call the function countDown(7)
	countDown(7);
	// And then print out the value returned by multiplyEach()
	console.log(multiplyEach());


表に書くことを学んだ。書いてみると、あー、そういうことかー！ってわかるのね。  
プログラミングで紙なんて使わないと思ってたけど、紙とペン、だいじだった。

![表を書け](http://farm9.staticflickr.com/8209/8178894649_88a590faca_z.jpg)

忘れないうちに [Project: Recursive Functions](http://www.codecademy.com/courses/javascript-lesson-149/0) もやっつけたい。