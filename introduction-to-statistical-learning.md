# Notes from "Introduction to Statistical Learning"



The following notes are based on the Work of James, Witten, Hastie and Tibshirani in their magnificent introduction to statistical learning.

Reference:

<cite>Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani. An Introduction to Statistical Learning : with Applications in R. New York :Springer, 2013. Print.</cite>



## The general problem formulation

Suppose we have a quantitative response $ Y $ and $ p $ different predictors $ X_1, X_2, ..., X_p $. Assuming a relationship between $ Y $ and $ X = (X_1, X_2, ..., X_p) $, we can write it in general form as  $$ Y = f(x) + \epsilon $$, where $ f $ is the *true underlying relationship* and  $ \epsilon $ is a *mean-zero random error term*.

Estimating $ f $ based on the observations is the process of **statistical learning**.​ 



### Prediction 

In prediction, for readily available $ X $, we try to obtain $ Y $, where we don't have it. Here, the *error term* averages to zero, than we can predict $ Y $ by $$ \hat{Y} = \hat{f}(X) $$. In Prediction, we see $ \hat{f} $ more as a *black box* and are interested in the actual prediction results.



__Excursion: reducible and irreducible error__

The error term in our model can be divided into the two above named categories. 

**Reducible error**: Is the inaccuracy of $ \hat{f} $ that introduces error, but **can be mitigated through an appropriate statistical learning method**. (--> the better the model, the less reducible error)

**Irreducible error**: :zap: Even if it would be possible to achieve a perfect estimate for $ f $, the prediction would still contain errors! This is because $ Y $ is also a function of $ \epsilon $, which **by definition can not be predicted using $ X $** (otherwise we would have it in X and introduce systematic error). 

But, why is the irreducible error > 0? The error term may contain unmeasured variables that are helpful for predicting $ Y $. The term may also contain unmeasurable variation (e.g. the general well-being of a patient on a day, which is hard to measure).



The two error term can also be shown mathematically.

$$ E(Y - Y)^2 = E[f(X) + \epsilon - \hat{f}(X)]^2 = [f(X) - \hat{f}(X)]^2 + Var(\epsilon) $$, where $ [f(X) - \hat{f}(X)]^2  $ is the reducible error that can be reduced by a "better" model. And $ Var(\epsilon) $ is the irreducible error that stem from the variation of the random error.



### Inference

In inference, we try want to find out how $ Y $ is affected by $ X_1, X_2, ..., X_p $. We want to understand the relationship between $ X $ and $ Y $ and how $ Y $ changes as a *function of* $ X $. As a result, we __do not__ see $ \hat{f} $ as a **black box**, but want to understand it's inner workings and the effect / influence of the different inputs into our model.

When trying to do inference, it is generally better to use a simpler model, since it's **explainability** is higher.



## Parametric models

Here we are trying to **estimate parameters**, hence **parametric models**. 

Steps in PM:

1) Make assumptions about model (functional form, shape, ...)

2) Fit / train the model (-> estimate the parameters)



:heavy_plus_sign: might be a good choice if we only have little date to model from (make it more simple)

:heavy_minus_sign: model usually does not fit the **true form** of f



## Non-Parametric models

No explicit assumptions about the functional form of $ f $, which make it possible to fit a wider range of possible shapes. Possible models could be *thin-plate splines* that have a *smoothness* factor which controls the ruggedness of the spline.

➖ very large number of observations is required



## Assessing Model Accuracy

$$ MSE_{training} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{f}(x_i))^2 $$ --> which is based on the training data, but we are interested in **how model performs on unseen data**. Since when continuing to fit the model on training data, we will **overfit** at some point as seen in the graph below. Training error decreases, where at a certain point the **test error increases**. This is the **generalization gap**, where the model overfits and does not generalize well anymore.

![training-vs-test](img\training-vs-test.PNG)

## The Bias-Variance Trade-Off

The U-shaped curce observed in the test MSE curves is a result of *two competing properties* of statisical learning: **Bias** and **Variance**. Mathematically, the two components of a model can be shown as such:



$$ E(MSE_{test}) = E(y_0 - \hat{f}(x_0))^2 = Var(\hat{f}(x_0)) + [Bias(\hat{f}(x_0))]^2 + Var(\epsilon) $$ , where $ x_0 $ stands for the test data.



:bulb: We need to choose a statistical learning method that achieves -> **low variance** and -> **low bias**!



**Variance** $Var(\hat{f}(x_0))$: Is the amount by which $ \hat{f} $ changes if **estimated with a different train data set**. Should not vary too much, but in general, more flexible statistical methods (in degrees of freedom) have higher variance.​ If method has high variance -> small changes in train data can result in large changes for $ \hat{f} $.



**Bias** $ [Bias(\hat{f}(x_0))]^2 $: Is the error that is introduced by approximating a real-life problem with a much simpler method. Generally: more flexible methods result in less bias.

![trade-off-bias-variance](img\trade-off-bias-variance.PNG)



As a general rule, the **more flexible** the methods, **variance will increase** and the **bias will decrease**. The relative change between the two determines whether the test MSE increases or decreases. As we increase the flexibility of methods, the bias tends to initially decrease faster than the variance increases. However, at some point increasing flexibility has little impact on bias but starts to significantly increase the variance. This is when the test MSE curves starts to increase and form it into its U-shape.

Also, as can be seen from the formulation of the $ E(MSE_{test})  $, even if the variance and bias of the model would be there, we would still have $ Var(\epsilon) $ influencing our predictions. 