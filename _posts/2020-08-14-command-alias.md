---
layout: post
title: Shortcut Commands for Terminal
tags: Dev
---

Sometimes I come across some terminal commands that comes handy frequently but takes minutes to type in, such as [finding the most used commands](https://jiaxigu.github.io/2019-07-09/most-used-commands):

	history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10

But I don't actually want to type this sh!t EVERY time I want to see my frequently used commands. Luckily, it's possible to save shortcut to commands. Here is how:

First, open the bash profile:

	vi .bash_prifle

Second, add alias and save the profile. The general grammar writes:

	alias {shortcut}="{original command}"

To assign the aforementioned command to, let's say, `history`, I can do:

	alias history="history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10"

And now I can type `history` instead of that whole spaghetti magic. Be sure to avoid any collisions when assigning the aliases.

## Refenrences

- [https://developer.aliyun.com/article/620474]()