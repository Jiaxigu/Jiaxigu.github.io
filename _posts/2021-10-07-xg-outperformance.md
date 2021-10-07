---
layout: post
title: Evaluating PL Strikers with xG Outperformance
tags: DS
---

In recent years, the term _Expected Goals (xG)_ has risen to prominence in football analytics. Being a low scoring game, the goals scored in a football game can be heavily influenced by luck, form or any other random factors, making it less valuable for data analysis. xG, on the other hand, indicating what will happen on an average day, provides with a rather clear insight.

The xG gives an expectation about if a shot would convert to a goal. For example, if a shot has an xG of 0.13, it means the shot has a 13% chance to score. The prediction thing is run by a deep learning model. The model learns from historical data and makes prediction by reviewing the result of shots taken from similar distance, angle, and defense pressure.

## xG Outperformance

_xG outperformance_ describes the percentile difference between the cumulative goals scored and the cumulative xG from a series of shots S.

```
xG outperformance = (cumulative goals from S / cumulative xG from S - 1) * 100%
```

We could use an example to further explain xG and xG outperformance: Robert Lewandowski had a total of 135 shots in season 2020/21, and the sum of each shot's xG is 32.08. It means Lewy is expected score 32.08 goals last season.

In fact, Lewy scored 41 goals. Then we can calculate his xG outperformance in the last season: 27.8% (8.92 "extra" goals scored above expectation, and divided by 32.08).

Obviously, higher xG outperformance means better scoring efficiency. If a player has a positive xG outperformance over a long period of time, his/her finishing ability should be better than league average.

## Data

I have scrapped the seasonal xG data until now for all players that have scored more than 45 goals in the Premier League since 2014/15. The following plot presents the cumulative xG outperformance for each player included.

![Plot1](https://raw.githubusercontent.com/Jiaxigu/Jiaxigu.github.io/master/assets/images/2021-10-07-xg-outperformance.png)

Also, you can find below the detailed ranking of each player. Mason Greenwood and Timo Werner are two undersampled(cumulative xG < 20) extreme values. 

![Plot1](https://raw.githubusercontent.com/Jiaxigu/Jiaxigu.github.io/master/assets/images/2021-10-07-xg-violin.png)

## Player notes

Son and Hazard are one league above everyone else. Out of these two, Hazard actaully looks much more amazing. He consistently outperforms xG, with left foot and right foot, inside and outside of the box. Don't forget he's not a pure striker - he dribbles, passes and cuts a lot. For Sonny, his long shot makes a big contribution to his xG outperformance score. He scored 17 goals outside of the box with just 6.3 xG!!

Kane's consistency is truly amazing. It's incredibly hard to stay just short of a 20% xG outperformance. Also, Martial is clearly mistreated by United fans. He is in fact the most reliable finisher at the Reds.

City's misery:

TBA

Finally, two cents on Greenwood and Werner:

It's universally acknowledged that undersampled, extreme values are not consistent. The stats will converge as they pick up games and shots. I also took a look at Werner's stats at Leipzig, and they are just fine! So, Werner will be fine. OR SOLD BY CHELSEA, HAHA.

## Further Notes

First of all, xG performance reflects only how clinical a player is. It doesn't correlate well with the player's ability to create chances.

Also, this model is overshadowed by the lack of data. I only managed to find seasonal data, while the match-specific data are behind a pay wall. As a result, I could only calculate mean value, instead of value distribution and confidence interval, for each player. 

I also noticed a vague anti-correlation between average xG per shot and xG outperformance. It seems that players are more likely to outperform when they do more low-xG shots, such as freekicks and long-range shots. I would like to check it out as soon as I'm guaranteed with more data.

## Reference

- [understat](https://understat.com/)
