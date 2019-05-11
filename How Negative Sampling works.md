# How negative sampling works?

Word2vetor prevails in today's Natural Language Processing.

The concept of "negative sampling" originates from the paper: Efficient Estimation of Word Representations in Vector Space.

And discussed in detail in : Distributed Representations of Words and Phrases and their Compositionality. This paper
proposes that "negative sampling" deals with the softmax which has trouble in calculating the term benith the dominator.
As an alternative, they use "negative sampling" as an alternative and they give another equation which only have some 
terms including a target term and several sampling term. The shape of the terms are like "log(sigmoid(term))".

But I found the paper arcane and I can't understand why the change the shape into sigma(log) from log(sigma).
And I can't understand where the sigmoid come from. Moreover, I found most explanations on the INTERNET does not deal
with the most puzzling part mentioned above.

But here goes the explanation:

The new terms are not the mathematical deductions from softmax, but a new Objective Function.

I mean. They changed the objective function!

The original highe loss like sigma(p*log(Softmax(x))) objective function 

is replaced by a hinge loss whose shape is like sigma(p*log(sigmoid(x))).

As they claimed:
>
>Thus the task is to
>distinguish the target word wO from draws from the noise distribution Pn(w) 
>using logistic regression, where there are k negative samples for each data sample.
>
