Q7: Whose gradient is used in GBDT?

A: In GBDT a sequence of trees are generated and for tree t. 
If we assume the loss function is l() and prediction of tree t is f_t(), then the gradient 
used in GBDT is the gradient of l(y_hat - sum{i from 0 to t-1}{f_i}) with respect to sum{i from 0 to t-1}{f_i}.
