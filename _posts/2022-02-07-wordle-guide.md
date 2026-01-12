---
layout: post
title: The Stats behind Wordle
tags: Featured
---

The puzzle game _Wordle_ have been trending for a while and hit headlines more recently when purchased by _New York Times_ for over 1 million USD. In _Wordle_, players need to identify a randomly generated 5-letter word in 6 attempts or less. Players learn hints about the letters and their placements after every attempt: green block means we have the right letter in right place; orange block means the right letter but in wrong place; black block means we get the letter wrong.

Simple game as it is, _Wordle_ is well designed in so many ways. I'm not intended to delve into these aspects today; instead, I'm more interested in the statistical aspect of the game.

## Letter frequency

Playing _Wordle_, or any other word puzzles, requires knowledge about letter frequency. From the corpora of [2315 possible solutions of _Wordle_](https://artofproblemsolving.com/news/articles/the-math-of-winning-wordle) as well as the [*1995 edition of Concise Oxford Dictionary*](https://www3.nd.edu/~busiforc/handouts/cryptography/letterfrequencies.html), letter `e` appears 36 and 57 times more frequent than letter `q` respectively. The plot below shows the frequency of each letter to feature in the solution. 

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-letter.png){: .center-image}

In _Wordle_, the difference in frequency could transform into different probability distribution of hints given. Imagine putting letter `z` at first (with `zebra` for example), the block has 0.1% probability to turn green, 1.4% orange (right letter in wrong place) and 98.5% black. By putting letter `r` at second (with `trace` for example), the block has 11.5% probability to turn green, 24.6% orange and 63.9% black. Given the distributions, it's not hard to understand that selecting letters of higher frequency provides more help to winning the game.

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-position.png){: .center-image}

## Optimal Way Out

Since the size of possible solutions (2315 words) is rather small, a [definitive, decision-tree like optimal solution](https://jonathanolson.net/experiments/optimal-wordle-solutions) to the game has been found by computer simulation with search heuristics. This strategy finds strong *sweepers* that divides possible solutions into many subgroups of similar size. In average, the strategy finds the answer with 3.42 iterations.

However, casual players are very unlikely to perform such decision process. For example, after a first attempt with `CRATE` (figure below), it's still hard for human to determine that `COMET`, `COVET`, `CHEST` and `CLEFT` are the only remaining options, not to mention that using `ABMHO` as the identifier is simply out of this world.

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-abmho.png){: .center-image}

## Strategy For Casuals

Casual players depend heavily on accumulated information to make guesses. The sheer number of successful blocks (green and orange) could be the key to a successful attempt. In this regard, `IRATE` comes atop with an expectation of 1.78 successful blocks.

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-irate.png){: .center-image}

A good strategy now is to keep winning out of mind in the first 2 or 3 attempts, and try to hit as many successful blocks as possible with *sweepers*. When planning the first 2 or 3 attempts collectively, we can use words combinations that cover the top 10 and 15 letters in terms of frequency, which ensure maximum value of successful blocks expected. `ROUTE` plus `SLAIN` is the top combo, while `CURLY`, `POINT` and `SHADE` make the perfect trio. They return 0.98 and 1.51 __green__ blocks respectively.

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-combo.png){: .center-image}

![](https://jiaxi-github-pages-photohost.oss-cn-beijing.aliyuncs.com/pyreneesalpaca/images/2022-02-07-trio.png){: .center-image}


## References

- [The math of winning _Wordle_](https://artofproblemsolving.com/news/articles/the-math-of-winning-wordle)
- [Letter frequencies](https://www3.nd.edu/~busiforc/handouts/cryptography/letterfrequencies.html)
- [Optimal _Wordle_ solutions](https://jonathanolson.net/experiments/optimal-wordle-solutions)

