---
layout: post
title: "Topping the Metaculus beginner tournament"
date: 2023-06-03
redirect_to: "https://blog.joshuablake.co.uk/p/metaculus-beginner-tournament"
---


Metaculus, a community-based platform known for its prediction competitions, recently hosted a beginner forecasting tournament. If you're new to this, forecasting tournaments involve making predictions on a wide range of topics, with the accuracy of those predictions determining the winners.
My involvement was rather successful, simply by applying the basic principles of forecasting.
In fact, I found myself, somewhat surprisingly, at the top of the leaderboard, despite my dwindling activity in the competition's closing weeks.
However, I did not officially win because I had a Metaculus account from before this year (previously, [Metaculus only required level 5 or below](https://www.metaculus.com/questions/15087/metaculus-beginners-on-points-leaderboard/), which I was at the start of the competition).
My basic strategy optimised performance for time spent: I spent 30 to 60 minutes on each question to set a base rate estimate for the majority of questions and rarely revisited them.

![Tournament leaderboard showing me first (score 1.289, second with 1.111, and third with 0.460, although third participated more than the top two).]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729102847.png)

As for my performance, it varied. I excelled in two questions, underperformed on one, and maintained an average run on the rest.

## My overall record

According to my binary question calibration, I demonstrated well-calibrated predictions, including all I've estimated on Metaculus.
Metaculus reported my underconfidence by 6% (I'm not quite sure what this metric means).
Assessing the data based on the graph is challenging due to the narrow bin size.
Nevertheless, the "well-calibrated" line falls within the 50% confidence intervals for nearly all bins, suggesting my calibration was not off the mark.
![My Metaculus binary calibration graph. Underconfidence is 6% based on 37 questions.]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729105651.png)

My continuous predictions look underconfident: there's too few questions that resolve in the tails of my distribution, which means that I'm placing too much probability mass there.
This is a very low sample size though, so I probably shouldn't take too much from it!
![My Metaculus continuous calibrate (cumulative distribution function).]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729105918.png)

## Assessing the stand-out questions

Two questions I did very well on.
For these questions, my edge was simply believing the base rate and not over-updating based on dodgy reporting or the questions framing.

The first question was [forecasting the number of lay-offs in the tech sector between 11th and 25th April.](https://www.metaculus.com/questions/15854/how-many-2023-tech-layoffs-by-april-25th/).
![History of predictions on the tech lay-off question. I forecasted towards the upper end of the range, much above the Metaculus prediction early on. I then adjusted downwards quite a bit in my central estimate, although still with a long upwards tail. The resolution was above the maximum.]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729132102.png)
Two weeks of lay-offs, based on historical averages, would have led to a number very close to the top end of the range you can predict, and a significant chance that it would be above the end of the range.
However, these announcements are very clustered: the numbers are dominated by a few rare events, which make the uncertainty high.
I'm not really sure why so few forecasters paid attention to this, but it provided me with lots of points so I'm not complaining!

The second question was [forecasting the number of coronation medals would be awarded by King Charles III](https://www.metaculus.com/questions/16529/king-charles-iii-coronation-medals/).
![History of predictions on the medals question. I predicted in-line with the Metaculus forecast at the time, but this quickly decreased due to circulating rumours in the press. The outside view one-out with the resolution being in-line with my initial estimate.]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729114600.png)
There were a bunch of newspaper reports that the numbers would be low, and that King Charles was trying to save money.
My take was two-fold: it would roughly be in-line with similar recent awards (e.g.: [400,000 issued for Queen Elizabeth II's platinum jubilee in 2022](https://en.wikipedia.org/wiki/Queen_Elizabeth_II_Platinum_Jubilee_Medal))  and very likely to cover all military personnel in the UK, if not the Commonwealth, although I did allow for a 10% chance that circulating rumours in the press of 10,000 could be correct.
The final number was 400,000, right on these estimates.

My worst question, by far, was [predicting the reported New York City homeless population on May 22nd 2023](https://www.metaculus.com/questions/17089/nyc-shelter-population-on-52223/).
![New York City homelessness question forecast history. My forecast on May 14th was correct but very uncertain, and I didn't update it.]({{site.baseurl}}/images/Metaculus-beginner-tournament/Pasted%20image%2020230729132251.png)
Here, I think my issue was simply not updating.
I forecasted about a week out, when there was some policy changes going through the system.
These changes' effects were probably clear a few days later.
If I had updated my forecast, I could have reduced the uncertainty and performed much better.

## Conclusion

_This section courtesy of ChatGPT. The tone is... Interesting..._

While this post doesn't offer any revolutionary insights, it serves to highlight the importance of following well-established forecasting principles in a tournament setting, like Metaculus's beginner tournament. The experience underscored the value of respecting base rates, regularly revising predictions, and acknowledging the fair criteria set by the organisers. This journey may not have ended with a formal victory, but the learning outcomes - embracing both our hits and misses as part of the forecasting process - make it a triumph in its own right. Every forecasting challenge is an opportunity for growth and this tournament has been no different.

_Comment on this post using [Google Docs](https://docs.google.com/document/d/1duenmX71VHsq7wSKxp9V5n8qHk-0e8As03ed_hWvwd4/edit) or [Twitter](https://twitter.com/JoshuaBlake_/status/1686067857224843276)._
