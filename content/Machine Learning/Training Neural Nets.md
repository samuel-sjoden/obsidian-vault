## Accessing The Performance of NNs
Eventually, the goal of a neural net is to be able to make predictions based on data that has not been accessed before. Depending on how we localize the variability of the data we train the [[Neural Nets]] on affects the generality of the predictions.

The larger the manifold of the state space that the training data occupies the more overlap there is with data that exists in the state space. 

> Data is finite. We need to be able to train, validate, and iterate on the model all with the same data pool
#### Validation Set
To evaluate a model, a subset of all availible data should be left as a 'test set' that ideally is representative of the state space of possible inputs. Human feedback can actually bais how well that our test set evaluates the model when we change the training data, then leaking information from the test set to the model.
#### Development Set
To control this we include another partrition, we create another subset of data called the dev set to improve where the net is weak. The test set is never looked into. Only the dev set is used to see where the model is failing to generalized.
### Underfitting and Overfitting
Natural data has some variance, so underlying trends may not perfectly match the data. The best possible fit is called the optimal fit. The more neurons or degrees of freedom availible, the tighter the model can capture the data. There is a critical amount of network complexity to ensure that the network can see the trend without not mapping to the data or mapping to the noise itself.

**Underfitting - High Bias**
With not enough degrees of freedom, the model is not able to capture the complexity of the data and will result in an underbias. 

The models prediction of the data has high loss

**Overfitting - High Variance**
If there are many many degrees of freedom, it will be able to match the data exceptionally well to minimize the loss function. This issue with this is that it starts to map to the noise. The model is unable to fit to the underlying data, and therfore cannot generalize well.

The model has so many parameters it captures the noise of the system. This is an [[Ill Conditioned Systems]] since with small changes in the input can result in large changes in the output.

### Quantifying Bias and Variance
If the loss function for a model is the mean squared error, the expectation value of the loss function can be decomposed into three components.
$$
\text{MSE}=\left< (\hat{f}-f)^2 \right>
$$

It can be decomposed into the **Bias, Variance, and irreducable error**
#### Bias
The bias explains how far off the models predictions are from the actual data
$$
\left< (\left< \hat{f} \right> -f)^2 \right>
$$
This depends on the output of the model and the actual data itself
#### Variance
This error is based of how different the models predictions are
$$
\left< \left(\hat{f}-\left< \hat{f}  \right) ^2 \right>  \right> 
$$
This term depends only on the model itself
#### Irreducable (Bayes) Error
This is the amount of noise present in the data. This is the absolute minimum that the loss function of our model can perform at.

## Training Strategies
If both the training error and validation error is high, that means that the model has high bias. It is underfitting the data and needs more complexity to capture the trend in the data.

If the model is able to predict the training data within baysian error, but cannot generalize to the validation data, it is likley overfitting the test data. Here you will either need more data, regularize or try a different NN arcitechture.

### Double Decent
There is some point deep beyond the overfitting where the complexity way surpassses the data say a multibillion parameter model mapping to a million dimensional problem, the performance starts improving again. This is not similar to other mathematical model like [[Fourier Series]] or [[Interpolation]] that do continue to overfit. 

The point of worst performance is just near when the complexity of the model is comparable to that of the dimension of the data. The size of the model required to see this effect is usually the limiting factor of reaching this effect expecially with incredibly high dimensional data.

### Error Analysis 
#### Binary Classification
There are many types of errors that can be used to tell how often correct and incorrect guesses are made.

##### Confusion Matrix


#### Regularization
If overfitting is noticed, the system can be regularized. To get sharp transitions that are able to rapidly output changes with high variance, large weights are required. 
To try to eliminate this artifact from producing we can add the size of the weights to the loss function to penalize the neural net for having large weights.

L1 regularization:
$$
\text{Cost} = \mathcal{L} + \sum|w_{i}|
$$
###### Dropout
Involves disengaging neurons to use the half brain to ensure that the entire network is used when making predictions.

#### Data normalization
If the scale of the data has large changes in one dimension, this will take time for the weights to adapt to the scaling of the data. This will also result in the learning rate varying in each dimension.

To normalize the input data you can center the mean of the data at zero and change the separation of the data by the average variance

Zeroing the mean:
$$
\mu:= \frac{1}{m}\sum_{i=1}^{m} x_{i}
$$
$$
x_{i}:= x_{i} - \mu
$$
Scaling by the variance:
$$
\sigma^2:=\frac{1}{m}\sum_{i=1}^{m} x_{i}*x_{i}
$$
$$
x_{i}:=\frac{x_{i}}{\sigma^2}
$$

#### Data Augmentation
To multiply the finite data, you can do a whole bunch of transforms to the data to create a new form of data.

#### Pruning
If weights are very small, you can remove them. 
Casting floats to integers makes operations much faster.
Keras.

