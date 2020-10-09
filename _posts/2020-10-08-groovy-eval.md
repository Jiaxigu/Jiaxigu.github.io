---
layout: post
title: eval() in Groovy
tags: Groovy
---

As a python fanatic, `eval()` and `literal_eval()` walked straight into my coding life and would never ever leave again. For me, this pair of beauty usually works as interpreter in data pipelines, enabling rule configuration from other systems. The `eval()` function exists in Groovy as well, and it deserves a mini intro.

## `Eval.me()`

`Eval.me()` allows expression evaluation without arguments. The expression can be compound, i.e. a collection of multiple expressions:

	def exp = "def a = 1; a + 2"
	println(Eval.me(exp)) // 3

## `Eval.x()`

`Eval.x()`, `Eval.xy()` and `Eval.xyz()` require fixed argument namespace in the expression and allow 1, 2 and 3 values respectively to be passed to the arguments.

	def val1 = 1.3
	def val2 = 1.5
	def exp1 = "x > 1.5"
	def exp2 = "x + y > 2"
	
	println(Eval.x(val1, exp1)) // false
	println(Eval.xy(val1, val2, exp2)) // true

## Refenrences

- [https://mrhaki.blogspot.com/2009/11/groovy-goodness-simple-evaluation-of.html]()
- [https://docs.groovy-lang.org/latest/html/api/groovy/util/Eval.html]()