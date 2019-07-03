Q: what is the difference between LSTM and LSTMCell?

A:
LSTM can process a batch of input, such as a list of list of embeddings. However, 
a LSTMCell can be intepreted as a LSTM that can only process one input.
In the CS224n assignment4's nmt model, LSTM is used as the encoder and LSTMCell is used as the decoder.
The reason for this treatment goes that the input are already known yet the output has to be done step by step since
the decoder need to know the output of a previous step.
