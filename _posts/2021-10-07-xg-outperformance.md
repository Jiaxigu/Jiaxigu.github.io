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

## Data

I have scrapped the xG data by season until now for all players that have scored more than 45 goals in the Premier League since 2014/15. The following plot presents the cumulative xG outperformance for each player included. 

![Plot1](https://raw.githubusercontent.com/Jiaxigu/Jiaxigu.github.io/master/assets/images/2021-10-07-xg-outperformance.png)

## Notes

This outperformance model is shadowed by the lack of data. I have only collected seasonal data for each player. More descriptive stats, such as confidence intervals, could be supplied if I could get access to the match data, which are behind a pay wall.

I also noticed a vague anti-correlation between the average xG per shot and xG outperformance. It seems that players are more likely to outperform when they fire more low-xG shots, such as freekicks and long shots. I would like to check it out if I'm guaranteed with more data.

## Reference

- [understat](https://understat.com/)
