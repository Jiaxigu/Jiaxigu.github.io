---
layout: post
title: The Twelve Balls Problem
tags: Dev
hidden: true
categories: Archive
---

Recently I caught up with a interesting math problem called [the twelve balls problem](https://puzzling.stackexchange.com/questions/183/twelve-balls-and-a-scale).

<!-- more -->

## Codes

Following is a piece of code as a simulated solver.

```python
# https://puzzling.stackexchange.com/questions/183/twelve-balls-and-a-scale
def run():
    # setup
    balls_weight = [1] * 12
    fake_idx = np.random.randint(0, 12)
    balls_weight[fake_idx] = np.random.randint(0, 2)+ 0.5
    print(balls_weight)
    
    # functions
    def weigh(idxa, idxb):
        # the simple weighing function
        # idxa, idxb being indexes
        # represent 3 results from scale (to left, equal, to right) of three-state boolean of -1, 0, 1
        left = [balls_weight[a] for a in idxa]
        right = [balls_weight[b] for b in idxb]
        res_func = lambda x: 1 if x > 0 else -1 if x < 0 else 0
        return res_func(np.sum(left) - np.sum(right))

    def three_ball_situation(ia,ib,ic, case_boolean):
        # this function solves a generic 3-ball situation with 1 step
        # ia, ib, ic being indexes
        # case True: either a/b has plus weight or c has minus weight
        # case False: either a/b has minus weight or c has plus weight
        # returns the fake ball index and weighing state: True for plus weight, False for minus weight
        res3 = weigh([ia], [ib])
        if res3 == 0:
            return ic, not case_boolean
        else:
            return ib if case_boolean^(res3 > 0) else ia, case_boolean


    # step 1: weigh balls 0~7
    res1 = weigh([0,1,2,3], [4,5,6,7])
    if res1 == 0:
        # balls 0~7 are good
        # step 2: weigh balls 9,10 to 8 and a good ball (0)
        res2 = weigh([0,8], [9,10])
        if res2 == 0:
            # ball 11 is fake
            # step 3: weigh ball 11 to a good ball (0)
            res3 = weigh([0], [11])
            return 11, True if res3 < 0 else False if res3 > 0 else 'MyMathFailedError'
        else:
            # step 3: three-ball situation with 9/10 in the same direction (based on step 2 result) against 8 
            return three_ball_situation(9,10,8, res2 < 0)
    else:
        # balls 8~11 are good
        # remove good balls and 3/6/7 (still questionable); switch sides of 4 and 2; finally add a good ball (8) to the right
        res2 = weigh([0,1,4], [2,5,8])
        if res2 == 0:
            # 0/1/2/4/5 are good
            # step 3: three-ball situation with 6/7 in the same direction (based on step 1 result) against 3 
            return three_ball_situation(6,7,3,res1 < 0)
        elif res1 == res2:
            # scale status didn't change, balls that didn't switch sides in step 1 and 2 (0/1/5) are questionable
            # step 3: three-ball situation with 0/1 in the same direction (based on step 1/2 result) against 5
            return three_ball_situation(0,1,5,res1 > 0)
        else:
            # scale status changed, balls that switched sides (2/4) are questionable
            # step 3: weigh ball 2 to a good ball (8)
            res3 = weigh([2], [8])
            return 4 if res3 == 0 else 2, (res2 > 0)^(res3 != 0)
```

## Simulations

... and here are some of the simulation results.

```python
for i in range(20):
    idx, res = run()
    print(f'fake pos = {idx+1}, fake is heavier: {res}')
```

```
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1.5, 1]
fake pos = 11, fake is heavier: True
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1.5]
fake pos = 12, fake is heavier: True
[1.5, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 1, fake is heavier: True
[1, 1, 1, 1, 1, 1, 1.5, 1, 1, 1, 1, 1]
fake pos = 7, fake is heavier: True
[1, 1, 0.5, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 3, fake is heavier: False
[1, 1, 1, 1, 1, 1, 1, 1, 1, 0.5, 1, 1]
fake pos = 10, fake is heavier: False
[1, 1, 1, 1, 1, 1.5, 1, 1, 1, 1, 1, 1]
fake pos = 6, fake is heavier: True
[1, 1, 1, 1, 1.5, 1, 1, 1, 1, 1, 1, 1]
fake pos = 5, fake is heavier: True
[1, 0.5, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 2, fake is heavier: False
[1, 1, 1, 1, 0.5, 1, 1, 1, 1, 1, 1, 1]
fake pos = 5, fake is heavier: False
[0.5, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 1, fake is heavier: False
[1, 1, 1, 0.5, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 4, fake is heavier: False
[1, 1.5, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 2, fake is heavier: True
[1, 1, 1, 1, 1, 1, 1, 1.5, 1, 1, 1, 1]
fake pos = 8, fake is heavier: True
[1, 1, 1, 1, 1, 1.5, 1, 1, 1, 1, 1, 1]
fake pos = 6, fake is heavier: True
[1, 1, 1.5, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 3, fake is heavier: True
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1.5, 1]
fake pos = 11, fake is heavier: True
[1, 1.5, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 2, fake is heavier: True
[1, 1, 0.5, 1, 1, 1, 1, 1, 1, 1, 1, 1]
fake pos = 3, fake is heavier: False
[1, 1, 1, 1, 0.5, 1, 1, 1, 1, 1, 1, 1]
fake pos = 5, fake is heavier: False
```

## Thoughts

The best part of the problem is probably not the solution itself, but how one can guide his way to it.
