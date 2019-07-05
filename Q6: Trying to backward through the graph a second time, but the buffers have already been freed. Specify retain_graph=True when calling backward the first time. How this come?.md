Q6: Trying to backward through the graph a second time, 
but the buffers have already been freed. 
Specify retain_graph=True when calling backward the first time. 

How this come?

A: This situation often occurs when you are using rnns and forget to have the code 

> hidden = hidden.data

when using loops in rnns.
