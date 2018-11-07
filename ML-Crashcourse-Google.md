# Machine Learning Crash Course from Google

Source: https://developers.google.com/machine-learning/crash-course


## Descending into ML

### Linear Regression

$ y' = b + w_i b_i $

### Training and Loss

**Empirical risk minimization**: ML algo builds model by examining many examples and attemps to find a model that minimizes loss. <br>
**Loss**: penalty for bad prediction -> how bad does model perform on a single example.

**L2 Loss** (squared error)

$ L_2Loss = \sum_{(x,y) \in D} (y - prediction(x))^2 $

--> sometimes it is useful to average over all examples, so divide out by $ \frac{1}{} $ --> MSE.

**Mean Squared Error (MSE)**: $$ MSE = \frac{1}{N} \sum_{(x,y) \in D} (y - prediction(x))^2 $$

!!! Although MSE is commonly-used in machine learning, it is neither the only practical loss function nor the best loss function for all circumstances. !!!

## Gradient Descent

**batch**: # examples in **one** iteration <br>
**Stochastic GD (SGD)**: only **one single example** per iteration (chosen randomly) <br>
+ simple <br>
- noisy

**Mini-batch stochastic gradient descent (mini-batch SGD)**: compromise between full-batch iteration and SGD, typically between 10 and 1,000 examples (chosen at random). <br>
+ reduce noise <br>
+ less computational load
