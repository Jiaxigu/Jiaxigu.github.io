---
layout: post
title: Command Shortcut for Terminal
tags: Dev
---

Sometimes I come across terminal commands that are handy frequently but take minutes to type in, such as [finding the most used commands](https://jiaxigu.github.io/2019-07-09/most-used-commands):

```shell
history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10
```

But I don't actually want to type this sh!t EVERY time I want to achieve that goal. Luckily, it's possible to save command shortcuts. Here is how:

First, open the bash profile:

```shell
vi .bash_profile
```

Second, add alias and save the profile. The command-line writes:

```shell
alias {shortcut}="{original command}"
```

To assign the aforementioned command to, let's say, `chist`, I can do:

```shell
alias chist="history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10"
```

And now I can type `chist` instead of that whole spaghetti magic. Be sure to avoid any conflicts when assigning the aliases.

## References

- [https://developer.aliyun.com/article/620474]()