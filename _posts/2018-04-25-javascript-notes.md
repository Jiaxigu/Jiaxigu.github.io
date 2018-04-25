---
layout: post
title: JS notes: ternary, const function and more
tags: Javascript
---

Recently I'm attacking the world of JavaScript - a treasure for the front-end devs but a pain for the data scientists. Here are some notes from my experience working with JavaScript...

## Ternary conditional operator

I explained [here](https://jiaxigu.github.io/2017-11-27/ternary-operator-python) how to do ternary operator in Python but things get more complicated in JavaScript. In the latest ES6 coding standards, JavaScript is much more simplified than its previous versions. Here is an example of ternary conditional operator:

{% highlight javascript %}
var price = 25;
var isExpensive = price > 20 ? true : false;
console.log(isExpensive) // >>> true
{% endhighlight %}

It replaces:

{% highlight javascript %}
var price = 25;
var isExpensive;
if (price > 20) {
	isExpensive = true;	
} else {
	isExpensive = false;
}
console.log(isExpensive)
{% endhighlight %}

For multiple ternary operator, the coding format looks like:

{% highlight javascript %}
var price = 25;
var origin = 'sweden';
var car = 
	price > 50 
		? 'porsche'
		: price < 10
			? 'seat'
			: origin === 'sweden'
				? 'volvo'
				: 'bmw'
console.log(car) // >>> 'volvo'
{% endhighlight %}

## Reference

- [Ternary conditional operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
