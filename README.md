# Digit-Recognition-using-CNN
Digit Recognition(MNIST Dataset) using CNN

Convolutional neural network model(tensorflow) for digit recognition using MNIST dataset.<br>
Achieved an accuracy of more than 99% on test set. 


                                                                                  Convolutional Neural network with 4 layers
                                                                                   Learning rate decay from 0.003 to 0.0001
                                                                                   Optimization Algorithm : AdamOptimizer
                                                                                 max-pooling of size [1, 2, 2, 1], stride = 2
                                                                                         dropout(keep_prob --> 0.75)

 · · · · · · · · · ·      (input data, 1 --> no. of channels)                          X [minibatch_size, 28, 28, 1]
 @ @ @ @ @ @ @ @ @ @      -- (conv. + max_pool) layer 5x5x1=>16 stride 1               W1 [5, 5, 1, 16]        b1 [16]          (5x5 -- size of filter, 1 -- input channel, 16 -- output channels)
     ∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶                                                                       Z1 [minibatch_size, 28, 28, 16]           
    input 28x28x16    --->   max_pool --> 2 x 2, stride 2 -- output  ----------->      P1 --> 14x14x16

   @ @ @ @ @ @ @ @        -- (conv. + max_pool) layer 5x5x16=>32 stride 1              W2 [5, 5, 16, 32]        b2 [32]          (5x5 -- size of filter, 16 -- input channels, 32 -- output channels)
       ∶∶∶∶∶∶∶∶∶∶∶∶∶∶∶                                                                        Z2 [minibatch_size, 14, 14, 32]
    input 14x14x32    --->   max_pool --> 2 x 2, stride 2 -- output  ----------->      P2 --> 7x7x32

        ∶∶∶∶∶∶∶∶∶∶∶                                                       ----------->    reshaped to p --> [minibatch_size, 7*7*32]
      \x/x\x\x/           -- fully connected layer (relu + dropout)                   W3 [7*7*32, 200]       b3 [200]        (200 --> no. of neurons in fully connected layer)
       · · · ·                                                                        Z3 [minibatch_size, 200]
       \x/x\x/            -- fully connected layer (softmax)                          W4 [200, 10]           b4 [10]         (10 --> output classes (0 to 9))
        · · ·                                                                         Z4 [minibatch_size, 10]
