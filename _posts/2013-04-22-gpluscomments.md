---
layout: post
category : selfstudy
tags : [selfstudy, googleplus]
title: "ブログにGoogle+ commentsを追加してみたよ"
date: 2013-04-22
comments: false
---

[+Jun Mukai](https://plus.google.com/u/0/102550604876259086885)と[+Kaori Kotobuki](https://plus.google.com/u/0/115492843550796478280/posts)さんと[+Maki Sawa](https://plus.google.com/u/0/103874480038402857629/posts)ちゃんが自分のブログにGoogle+ comments貼っててうらやましかったのでわたしも貼っつけた。BloggerでもMTでもなくて、JekyllとGitHub Pagesのブログ。

本家。  
[Official Blog: Bringing Google+ Comments to Blogger](http://googleblog.blogspot.jp/2013/04/bringing-google-comments-to-blogger.html)  
参考記事。  
[How to add Google+ Comments to any website - Browsing the Net](http://browsingthenet.blogspot.jp/2013/04/google-plus-comments-on-any-website.html)

これの1を試したら、  
The frame requesting access has a protocol of 'https', the frame being accessed has a protocol of 'http'. Protocols must match.  
ていうエラーが出てポストできなかった。  
If you prefer to load Google+ Comments dynamically, insert this HTML code: 
のコードだと動いた。

{% highlight perl %}
<script src="https://apis.google.com/js/plusone.js">
</script>
<div id="comments"></div>
<script>
gapi.comments.render('comments', {
    href: window.location,
    width: '624',
    first_party_property: 'BLOGGER',
    view_type: 'FILTERED_POSTMOD'
});
</script>
{% endhighlight %}

なんでだろー。でも今日はねます。中途半端でごめんなさい。


