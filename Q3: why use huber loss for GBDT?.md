Q3: why use huber loss for GBDT?

A: GBDT usually use huber because huber behaves much more robust for outliers.

we know that in huber loss if the predicter and the real value have an difference larger than

delta, a certain valve value, then the loss of delta*(abs(y_hat-y) - delta/2) not the loss of 1/2(y_hat - y)^2 if abs(y-delta) > delta.
