---
layout: post
title: "My doubts about longtermism"
date: 2023-06-03
---

["Longtermism is the view that we should be doing much more to protect future generations."](https://www.williammacaskill.com/longtermism)
The philosophy has gained a large prominence within Effective Altruism (EA)[^EA-and-longtermism], and now appears to consume most of the discussion and energy within the movement, even if not most of the money.

[^EA-and-longtermism]: Why exactly this is isn't clear to me. It might be a founder effect, in that MacAskill was very involved in early EA and then went on to be majorly involved in longtermism (possibly because this all happened in the University of Oxford philosophy department). It might be that EA skews utilitarianism, which somewhat naturally leads to longtermism. It might be that MacAskill and others involved in early EA were convinced by longtermist arguments. This would be interesting for someone to dig into.

- Will MacAskill, arguably the biggest proponent of longtermism, [summarises](https://twitter.com/willmacaskill/status/1520107730626785280?lang=en) the argument for it as:

1. Future people count.
2. There could be a lot of them.
3. We can make their lives go better.

On the face of it, this is a convincing argument.

However, this post outlines my objections to it, summarised as:

1. Future people count, but less than present people.
2. There might not be that many future people.
3. We might not be able to help future people much.

To this, I will add a fourth: there are trade-offs from this work.

## Disclaimer

I am not a philosopher, and don't know much about philosophy (I am trying to learn).
This is my best thinking on longtermism, and why my credence is not high enough for it to be the major factor determining my career choices (as 80,000 hours advocates).

I should probably highlight I've not read What We Owe the Future[^books], but having talked to many people I don't think there is much in there that would change my mind.

I would __love__ to be told why my musings here are wrong, please [Tweet](https://twitter.com/JoshuaBlake_/) or [email](mailto:joshbblake@gmail.com) me!

[^books]: I'm bad at both starting and finishing books. I tend to overthink starting them (because I read so few that it feels like a big decision), and don't finish them. I'm not sure why, because I read a lot of shorter articles, Tweets, etc. My best guess is that it feels like a big commitment to pick up a book so I need a large block of time. Any suggestions on reading more books and less Twitter would be welcome.

## Future people count, but less than present people

The statement "I have a stronger ethical obligation to my immediate family more than a stranger" is deeply intuitive to me, and I would suggest most people; full impartiality is an ethically controversial view.
My ethical intuition points towards something like a network[^network].
The more connections to an individual, the stronger the ethical obligations.
In general, you'll be reasonably connected to those alive today ([even those geographically far](https://en.wikipedia.org/wiki/Small-world_experiment#Current_research_on_the_small-world_problem)) but as you span across time these connections will get weaker[^time-distance].
Therefore, we should somewhat discount the effects on people far into the future.

[^network]: Strictly, a weighted network such that some connections are more important than others. Then your obligation to someone is a monotonically decreasing function over the shortest distance to them.

[^time-distance]: This argument is based on distance to an individual, not absolute time: I claim your ethical obligation to people in the past is also less than to those in the future. In particular, this is agent-relative: I'm not claiming that future or past people have less worth intrinsically. Rather, that our moral obligations to them are less.

On the other hand, exponential discounting seems pretty wrong.
The classic example is that [even a 1% rate of discounting leads to Tutankhamun considering his own welfare as more important than the total of all humans alive today](https://80000hours.org/podcast/episodes/why-the-long-run-future-matters-more-than-anything-else-and-what-we-should-do-about-it/).
This also seems implausible.

I think there's some middle ground here: we should not count our contributions to future people's wellbeing as equal to that of people alive today, but we shouldn't discount as strongly as exponential.
Personally, something roughly logarithmic makes sense[^discount-function].

[^discount-function]: My initial thought is that discounting $t$ years from now something like $\left(1 + \log_{100}(t+1) \right)^{-1}$ seems reasonable.

## There might not be that many people

Most longtermists believe that we face a high probability of extinction over the next century.
[As David Thorstad has recently pointed out](https://globalprioritiesinstitute.org/wp-content/uploads/David-Thorstad-Existential-risk-pessimism-.pdf), assumptions over the baseline rate of risk are very influential on how much longer you expect humanity to last for given a certain reduction in extinction risk.
The basic conclusion is that, assuming you think extinction risk is currently high, standard longtermist estimates of future numbers of people are several order of magnitude too high, and longtermist interventions [no longer look obviously more cost-effective than simpler interventions such as bed nets](https://ineffectivealtruismblog.com/2023/02/04/existential-risk-pessimism-and-the-time-of-perils-part-7-an-application/)[^time-of-perils].
Be wary here though, how risk changes is [weird, non-linear, and non-intuitive](https://twitter.com/JoshuaBlake_/status/1638546433367212032).

[^time-of-perils]: It is possible to rescue longtermism with the Time of Perils hypothesis: that we live in a uniquely perilous time, and soon we will see dramatic reduction in extinction risk. Yet this would be extremely surprising (we just happen to be alive at this time). [Here's some discussion on that.](https://forum.effectivealtruism.org/posts/N6hcw8CxK7D3FCD5v/existential-risk-pessimism-and-the-time-of-perils-4?commentId=AASmenGnzBhvWQKLy)

Furthermore, there's often an (implicit or explicit) assumption that (assuming we do not go extinct) we will have vastly more humans across the stars and be vastly happier.
When I look at the suffering in the world today, I do not find the claim that humans will be much happier in the future compelling.
I ask what is bigger: the gap between the billions in absolute poverty today, and those of us in the rich world; or the gap between the current rich world and the happiest possible humans?
The answer seems pretty uncertain to me, but my intuition is that the former gap is probably bigger.

## We might not be able to help future people much

The idea that we can take actions that will predictably and significantly improve the lives of people centuries or millennia  in the future is quite bold on the face of it.
[We struggle to predict the consequences of our actions even decades into the future.](https://en.wikipedia.org/wiki/Unintended_consequences#Perverse_consequences_of_environmental_intervention)
Well-meaning global health interventions that seem convincing to funders [can be a bad idea](https://en.wikipedia.org/wiki/Roundabout_PlayPump).
Early EA thinking is heavily intertwined with GiveWell, who systematically seek out high-quality evidence to combat this.
For longtermism, rarely is any of this possible.

For these reasons, among others, longtermists tend to focus on [existential risks](https://futureoflife.org/existential-risk/existential-risk/): those that would cause human extinction, or affect humans so greatly that we could not return to our current standard of being[^x-risk].
This seems plausible, and preventing human extinction is unambiguously good.

[^x-risk]: What exactly is classed as an x-risk isn't clear, nor consistent between authors. Extinction, enslavement of humans (to aliens, artificial intelligence, or some other beings), or permanent absence of civilisation are generally considered to qualify. Ord, in his book The Precipice, also includes anything large enough that the long-term potential of humanity is limited; this definition appears to depend heavily on the idea that humans would (by default) be extremely happier in the future and that removing this potential is of similar magnitude to extinction. I think this claim needs further justification.

Yet, most well-studied risks do not seem to be likely enough for us to be that concerned about them (e.g.: meteor strikes).
Therefore, the focus turns to less well-understood risks, most prominently the risks from artificial general intelligence or yet-to-be-invented biological weapons.
This process can be referred to as [regression to the inscrutable](https://ineffectivealtruismblog.com/2023/02/18/academics-review-what-we-owe-the-future-part-3-rini-on-demandingness-cluelessness-and-inscrutability/): the arguments become less empirical and more based on intuitions or unverifiable claims, and hence near-impossible to argue against.


## Remember the trade-offs

For me, the crucial insight of EA is that we have limited resources (time and money) that we should try and use to do as much good as possible.
This requires considering the relative value of different actions we can take.
Longtermism commits us to using these resources to help far-off humans, necessarily at the cost of those alive today.

With the simple argument for longtermism, the value of the future is extraordinarily high (say $10^{11}$ humans), which means that you can easily justify reducing the risk of extinction on cost-effectiveness grounds using standard metrics.
This is true even with not very high credence in longtermism, a lot of uncertainty over the actions you take, and more.
Yet, once you start discounting future humans and/or doubting the number of them, these considerations matter a lot.

## Conclusion

Longtermism is superficially compelling to me.
However, the longer I think about it, the more objections I find.
None of these are on its own insurmountable for the theory, however, combined, they mean I am hesitant to use it as the primary ethical theory guiding my actions.

EA generally approves of [reasoning with best guesses](https://slatestarcodex.com/2013/05/02/if-its-worth-doing-its-worth-doing-with-made-up-statistics/), I agree (at least, you should consider them).
That principle should be extended to longtermist interventions, and those advocating for large amounts of resources to go there should make their calculations clear.

_Discuss this post on [the EA forum](https://forum.effectivealtruism.org/posts/vuD4H7ziqLuPMGJYF/linkpost-my-doubts-about-longtermism), as [a Google Doc](https://docs.google.com/document/d/1_GeU6DodNMhnNAKINjvbuwKLvwts_weta2ZdyzWLKZY/edit?usp=sharing), or on Twitter._