Source:
> https://stats.stackexchange.com/questions/354484/why-does-xgboost-have-a-learning-rate

## Why does XGBoost have a learning rate?

Description of the question: the XGBoost docs have a theoretical introduction to XGBoost and don't mention a learning rate anywhere. So 
does it has the same meaning as Neural Net's "time step"?

## Answer:

Further explanation can be found in "XGBoost: A Scalable Tree Boosting System" by Tianqi Chen, Carlos Guestrin.

> Besides the regularized objective mentioned in Sec. 2.1, two additional techniques are used to further prevent overfitting. 
> The first technique is shrinkage introduced by Friedman [11]. 
> Shrinkage scales newly added weights by a factor η after each step of tree boosting. 
> Similar to a learning rate in tochastic [sic] optimization, 
> shrinkage reduces the influence of each individual tree and leaves space for future trees to improve the model.

We can consult the citation for further information. In "Stochastic Gradient Boosting," Friedman writes

> that the "shrinkage" parameter 0<η≤1 controls the learning rate of the procedure.
> Empirically (Friedman 1999), it was found that small values (η≤0.1) lead to much better generalization error.

(Except that I've edited the quote to use a different symbol for clarity and consistency with the rest of this thread.)

As with any regularization technique, people use it because it improves generalization error on their modeling tasks. 
I'm not aware of a study which examines whether the learning rate parameter is strictly necessary in the context of XGBoost 
(but I would be interested to read one!). 

Based on the way the "XGBoost: A Scalable Tree Boosting System" paper is written, 
it seems that the authors did not conduct such an analysis themselves, 
instead relying on previous results for other boosting algorithms.

Since the Friedman paper is also discussing the effects of adding additional randomization to boosted trees 
(e.g. bootstrapping), it seems reasonable to surmrise that in the context of random subsamples, 
you would not want early trees to dominate the classification decision, 
since those early trees are just specific random samples of the entire training data. 
Instead of having all subsequent trees be strongly influenced by the peculiarities of the first few random samples, 
introducing the "learning rate" seems like a clever way to down-weight the trees.

Speaking from personal experience, 
the difference between using a learning rate of 1.0 and a smaller learning rate like 0.1 is that models 
with the larger learning rate rapidly reduce the loss, 
but also rapidly reach a plateau. 
Here's an example comparing the same models on the same data with different learning rates. 
The smaller learning rate more slowly declines, and it attains a lower loss.


which is a math-y way of saying that at round m, 
the prediction function is the previous round's prediction Fm−1 plus a scalar multiple η of the new prediction. 
The expression γlm1(x∈Rlm) represents the solution to an optimization and 
an indicator function for whether x is a member of that region.
