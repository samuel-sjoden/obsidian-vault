## Convolution
The [[Convolution]] is a mathematical process where two signals that are passed over each other. In the frequency domain, convolution of two signals is just multiplication. This can be used to pick out frequencies in a signal. 

In an impulse, all frequencies are present. Recording it's response tells you the systems response to all frequencies. 

>[!Question]
> How does the impulse contain all frequencies? I would assume it just has an arbitrarily high frequency

Convolution can also be thought of a series of dot products between the signals which is why the output can tell you the similarity of the functions.

#### The Kernel
When the kernel matches the signal being processed, the output is large, when they do not match well, the output is small. Depending on the kernel selected, you can change what the output highlights.

The output of the convolution is maximized when the feature that the kernel is looking for is maximized. In this way, the kernel is filtering for features.

In the context of neural networks, the kernel is what convolutional [[Neural Nets]] try to optimize.

> It is important that the kernel has a 'center' meaning that the pixel size is odd
## Convolutional NN

Neural networks take in the image as an input and will perform various convolutions to the image with various kernels that the neural network will tune for. Then the next layer will take this output as the input and the process continues for each layer of the NN. Each time a smaller kernel is passed over the image, the size of the image decreases. This shrinking is because the edge values produce undefined values because there is no external points.


The complexity of the filter increases with the depth of the neural network.
Each colour channel gets their own kernel. Each kernel produces a new image. Then a linear bias function is applied to the pixels. Finally a non-linear transform is applied. 

You can have multiple filters/ sets of kernels in each layer of convolution. Each layer becomes its own channel

> [!Question]
>  What is the function of a pooling layer? How does it work?

Once all of the filters have been applied, the image data is unraveled and is input into a regular NN. Each of the values in this array is scaled by a weight. Just like a regular neural net, the last neuron has an activation node to produce the desired data.

#### Advantages of Convolutional NN
Instead of performing convolutions to an image, we could have flattened the image data into an array and feed it into a fully connected neural network. To have sufficient neurons to capture the complexity and amount of data the amount of parameters becomes massive.

Convolutional neural networks leverage the patterns that arise in natural images since only a very small subspace of possible data combinations for pixels are found in natural images.

Convolutional images can capture these patterns by looking around at nearby pixels, so they require significantly fewer parameters.

### Hyperparameters

##### Stride
If the image is very high resolution, the same regions capture the same data. To reduce the amount of computations required you can take 'strides' by skipping over pixels.

##### Padding
If you want to retain the size of the image, you need to pad the edge layer with a fake layer of pixels

>[!Question]
> How do you select what these pixels look like?
##### Max Pooling
After each layer of convolution, we perform a max pooling. Since were the kernel is finding things that match their filter best, the only things we care about is were the output is maximized. This reduces the amount of data to process. 

There is some drawbacks though since you are volunteering data away for the sake of faster training and fewer computations.


>[!Question]
> Is there any other two dimensional data that convolutional NNs can be used for?
> What about of arbitrary dimensional problems. Like making a song.


