# Distributions Cheatsheet

The following notes are based on the blog post **"Common Probability Distributions: The Data Scientist’s Crib Sheet"** by **Sean Owen** (@sean_r_owen) on the **cloudera engineering blog**.

Reference:

https://blog.cloudera.com/blog/2015/12/common-probability-distributions-the-data-scientists-crib-sheet/



# Common Distributions Network (as PDF)

![distributions](C:\Users\tberger\yellow-brick-road-to-MrLd-city\img\distributions.png)



## Bernoulli & Uniform [discrete]

![bernoulli_uniform](C:\Users\tberger\yellow-brick-road-to-MrLd-city\img\bernoulli_uniform.PNG)

**Bernoulli**:

* model **1** *"coin toss"*, only two possible outcomes (heads/tails)
* $ p $ probability of success and $ 1 - p $



**Uniform**:

* e.g. rolling fair die &rarr; *all outcomes equally likely**



## Binomial & Hypergeometric [discrete]

![binomial_hypergeometric](C:\Users\tberger\yellow-brick-road-to-MrLd-city\img\binomial_hypergeometric.PNG)



**Binomial**: &rarr; **"with replacement"**

* multiple Bernoulli experiments &rarr; e.g. multiple coin tosses &rarr; *"With $n$ tosses: How many times does it come up heads?"* or *"Drawing $ n $ balls (black/white) **with replacement** from an urn. How many are black?"*
* $n$  number of trials,  $p$  probability of success

* each trail is **independent** and has **same probability of success**



**Hypergeometric**: &rarr; **"without replacement"**

* Drawing $ n $ balls from urn **without replacement** &rarr; probabilities **not independent**
* **should come to mind when picking out a significant subset of a population as a sample.**
* if number of balls relatively large to number of draws $ n $ &rarr; binomial & hypergeometric become similar (chances change less with each draw)



## Poisson [discrete]

![poisson](C:\Users\tberger\yellow-brick-road-to-MrLd-city\img\poisson.PNG)

* **count events over a time given the continuous rate of events occurring** --> heading towards  infinitesimally small time slices in which the probability of a event is infinitesimal --> limit results in Poisson
* $ \lambda $ - average rate, **NOT** by $ n $ and $ p $ (in simple analogy $ \lambda = np $)

* queue processes: packets arrive at router, customers calling, ...



## Geometric and Negative Binomial

