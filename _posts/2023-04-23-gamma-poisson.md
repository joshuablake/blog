---
layout: post
title: "Improve your forecasts of events: use the gamma-Poisson model"
date: 2023-04-23
---

Forecasters often strive to predict the rate at which events occur[^rate]. However, traditional models used by forecasters, such as Laplace's rule (based on the beta-binomial model) have their limitations. These models are sensitive to the choice of scale (e.g., whether time is measured in years or months) and do not accommodate multiple events occurring within a single time period.

[^rate]: The rate of an event is the average (mean) number of events that occur per unit time. For example, the number of births per year or pandemic per decade. 

In 2022, Jamie Sevilla and Ege Erdil published a [blog post](https://epochai.org/blog/a-time-invariant-version-of-laplace-s-rule) that proposed a more robust alternative: the gamma-Poisson model.
This model is time- or scale-invariant, meaning that the choice of scale does not affect the results.
In this post, we will delve deeper into the gamma-Poisson model, exploring its assumptions and how to fully utilise the posterior predictions, and finally recommending an alternative to Sevilla and Erdil's suggested prior.

There are three main recommendations in this post.

1. Consider the assumptions behind your model, particularly that the rate of events is constant and that the times between events are independent.
3. Use the full posterior, including both the uncertainty in the event rate and the inherent randomness in when events occur, when making forecasts.
2. Consider the $\text{Gamma(1/3, 0)}$ prior when no prior information is available (recommended by [Kerman (2011)](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-5/issue-none/Neutral-noninformative-and-informative-conjugate-beta-and-gamma-prior-distributions/10.1214/11-EJS648.full) as a "neutral prior"), rather than the $\text{Gamma}(1, 0)$ recommended by Sevilla and Erdil.

## The gamma-Poisson model

The gamma-Poisson model is probably the simplest possible model for events occurring in continuous time.
The gamma refers to the distribution for the rate of events, and the Poisson to the distribution for how events occur conditional on the rate of events.
It requires only three assumptions:

1. Our prior belief for the rate of events can be represented as a gamma distribution.
2. The rate does not change over the period of time we are analysing.
3. The events follow a homogeneous Poisson process, meaning that events are independent and the chance of future events is not affected by past events.

The gamma distribution has two parameters: the shape ($\alpha$, the Greek letter alpha) and the rate ($\beta$, the Greek letter beta).
We write this distribution as $\text{Gamma}(\alpha, \beta)$. Both parameters must be greater than zero to ensure a proper distribution[^proper].
When used as a prior distribution, the parameters have intuitive interpretations: $\alpha$ represents the number of observed events, and $\beta$ denotes the length of the observation period.
As long as we are consistent in our analysis, the choice of units for $\beta$ is irrelevant, ensuring that our model is time- or scale-invariant.

[^proper]: A proper distribution fulfils the requirements of a probability distribution: the probabilities are never negative, and the sum of probabilities across all outcomes is 1. [↩](https://chat.openai.com/c/e51d8622-af05-48e7-80e5-fb73729bc4d4#user-content-fnref-proper)

One convenient property of the gamma-Poisson model is that the posterior distribution for the rate of events will also be a gamma distribution[^conjugate]. This allows us to easily write down our posterior beliefs. If our prior distribution is $\text{Gamma}(\alpha, \beta)$ and we observe $x$ events over $T$ time periods, our posterior becomes $\text{Gamma}(\alpha + x, \beta + T)$. A useful forecasting quantity is the probability that there are no events in some future period of length $t$, which is $\left( \frac{\beta+T}{\beta+T+t} \right)^{\alpha+x}$.

[^conjugate]: This is because the gamma and Poisson distributions are [conjugate distributions](https://en.m.wikipedia.org/wiki/Conjugate_prior).


## Using the posterior distribution for forecasting

When forecasting from the gamma-Poisson model, there's two reasons for our uncertainty.
First, we are unsure of the underlying rate of events, represented by our posterior gamma distribution.
Second, the process has some inherent randomness over when the events occur; that is, even if we knew the underlying rate, we still would not know how many events will occur in any period.

Often, a point estimate is taken for the first of these which understates our uncertainty.
This section will explain how to take both into account for several circumstances of interest.

### The rate of events

The gamma-Poisson model provides us with a posterior distribution for the rate of events: $\text{Gamma}(\alpha+x, \beta+T)$[^gamma].
The mean of this distribution, $\frac{\alpha+x}{\beta+T}$, represents our updated belief about the average rate of events occurring in a given time period.

[^gamma]: Be wary that an alternative parameterisation of the gamma distribution is sometimes used, which has $1/(\beta+T)$ as the second parameter. Check the documentation for any software package or that you get the correct mean. 

If we want to forecast the number of events in the next $t$ time periods, we also need to take into natural stochasticity in the process.
Consider that, even if we knew the rate of events exactly, we would still have some uncertainty over how many events will occur.
To take into account both our uncertainty over the rate of events and this stochasticity, we should use our posterior predictive distribution.
Under the gamma-Poisson model, this is $\text{NegativeBinomial}(\alpha+x, \frac{\beta+T}{t+\beta+T})$[^negbin].
The mean of this distribution, $\frac{t(\alpha+x)}{\beta+T}$, represents our expected number of events in the next $t$ time periods.

[^negbin]: Be wary that an alternative parameterisation of the negative binomial distribution is sometimes used, which has $t/(t+\beta+T)$ as the second parameter. Check the documentation for any software package or that you get the correct mean. 

### Time between events

The mean time between events is one over the rate of events (eg: if the rate is two per year, the mean time between events is half a year).
Our posterior here is $\text{InverseGamma}(\alpha + x, \beta + T)$.
The mean of this distribution is only defined if $\alpha + x > 1$, which (if you follow my recommendations for setting a prior) occurs when you've observed one event.
Intuitively, if we haven't seen any events, then we have some belief that the event and hence an infinite time between events.
When the mean is defined, it is $\frac{\beta+T}{\alpha+x-1}$.

Again, we get a posterior predictive distribution for the time until the next event.
Here is is: $\text{Lomax}(\alpha+x, \beta+T)$, which has the same mean as the previous InverseGamma.

### Probability of no events

Finally, we often want to know the probability that there are no events in a period of length $t$.
This can be derived from either the negative binomial of lomax distributions above, in either case giving:
$$
\left( \frac{\beta+T}{\beta+T+t} \right)^{\alpha+x}
$$
## Choosing the prior

The choice of our prior, specifically the values of $\alpha$ and $\beta$, can be quite influential if we have not observed many events (certainly less than 5, although even up to around 10). When we have relevant information (e.g., a suitable reference class), we should choose these parameters to reflect that information. However, in cases where no applicable information is available, we may want a "reference" or "objective" prior that is broadly applicable.

### Acceptable choices

Any suitable reference prior should have $0 < \alpha \leq 1$ and $\beta = 0$ to satisfy the following three principles.

1. Ensure that our posterior distribution is always proper, requiring $\alpha > 0$ and $\beta \geq 0$[^proper-posterior-requirements]. 
2. Avoid choices which cause changing inference if we change scales. As soon as we choose $\beta > 0$, the choice of scale matters, which is exactly what we want to avoid. Therefore, we should choose $\beta = 0$ and decide on $\alpha$.
3. If we have not observed any events, we should consider the single most probable outcome (the posterior mode) to be that the rate of events is 0, requiring $\alpha \leq 1$.

[^proper-posterior-requirements]: A proper posterior requires $\alpha + x > 0$ and $\beta + T > 0$. As long as we have observations for a non-zero amount of time, then $T>0$ and hence $\beta = 0$ is valid. However, we cannot guarantee that we observe an event (we might have $x=0$) which requires the strict inequality $\alpha > 0$.

### Specific choices

Several recommendations have been made for choosing $\alpha$.
Note that if $x$ is larger than about 5 or 10, the recommendations will yield similar results, so the choice is not critical.
If you have fewer events, I would recommend trying $\alpha = 1$ and $\alpha = 1/3$ to check how sensitive your results would be to this assumption for the specific quantities you care about.

Sevilla and Erdil recommended $\alpha=1$ because it closely resembles Laplace's rule and provides the best point estimate of the time between events (in expectation).
However, it tends to overestimate the rate of events significantly[^rate-vs-time-expectation].
This prior will mean that the expected rate of events is always noticeably higher than the observed rate.
Furthermore, there is quite a large posterior probability that this rate is higher (see the figure below).

[^rate-vs-time-expectation]: The difference here is intuitively confusing but can be explained due to considering what happens when events are rare. Here, the expectation of the time between events will greatly be affected by how much you believe that very large values of the time between events is possible. Furthermore, due to the lack of data, this belief is largely driven by your prior. Therefore, for an accurate mean (across all possible value of times between events) you prefer to underestimate the time between events, or equivalently overestimate the rate of events. This problem only occurs when considering expectations.

Kerman (2011) recommends $\alpha = 1/3$ because it implies that the true rate is equally likely to be greater or lower than $x/T$ for all values of $x$ and $T$, as long as $x \geq 1$ (at least one event observed).
This is because the median of a gamma distribution with parameters $a$ and $b$ is well approximated by $(a - 1/3)/b$.
Intuitively, this seems reasonable: if we have seen $x$ events in $T$ time periods, we should think it is just as likely that the mean rate is $x/T$.

Another popular choice is to make $\alpha$ very small, say $10^{-6}$.
This makes the prior pretty flat, and approximates the "scale-invariant" prior that Sevilla and Erdil want to use but do not due to creating an improper posterior.
Furthermore, it minimises the mean squared error in estimating the rate of events.
However, this prior places far too much probability mass on extremely small rates of events before we observe one.

{% include captioned_image.html url="/images/gamma_poisson_prior_plot.png" description="Figure 1: the posterior probability that the true event rate is greater than the observed rate based on the number of events that have occurred, $x$, the value of $\alpha$ in the posterior (for $x \geq 1$), and $\beta = 0$. Note that the choice of $\alpha = 1/3$ gives a approximately 50% probability for all values, which agrees with our intuition. Due to the scale-invariant nature of the gamma-Poisson model, these probabilities hold no matter what time period the events have occurred over. All lines shown will converge to 50%, however if $\beta > 0$ then they would converge to 0." %}

In cases where no events are observed, we must carefully consider the behaviour of the model.
Our observations provide no lower bound on the rate of events, and this information comes only from the prior.
One question to consider is, after observing no events for $t$ time, what is our posterior probability that the rate is less than $1/t$? Intuitively, we would expect this probability to be fairly high, certainly greater than 50%.
Kerman argues that it should be closer to 100% than 50% (i.e., greater than 75%), requiring $\alpha < 0.72$.
For $\alpha = 1/3$, the probability is 90%, and for $\alpha = 1$, it is 63%.

Overall: $\alpha \approx 0$ and $\alpha = 1$ are the best choices for estimating the rate of events and time between events respectively.
However, neither perform that well when we have not seen any events (especially $\alpha \approx 0$), and will perform poorly when we care about the parameter that the prior performs poorly on.
Choosing $\alpha = 1/3$ provides a reasonable trade-off between the two, and has the additional desirable property that, whenever we have observed at least one event, we think that the rate of events we've observed ($x/T$) is equally as likely to be too high as too low.

## Conclusion

Sevilla and Erdil correctly pointed out that using Laplace's rule for a continuous observation (such as time) leads to inconsistencies.
Here, we've laid out some details of the assumptions and use of this model.
I'd strongly recommend you to make use of the full posterior distribution for your forecasting, and consider a $\text{Gamma}(1/3, 0)$ prior.

Bonus: Kerman (2011) argues, for essentially the same reasons given here, that we should use a $\text{Beta}(1/3, 1/3)$ rather than a $\text{Beta(1, 1)}$ prior for probabilities.
