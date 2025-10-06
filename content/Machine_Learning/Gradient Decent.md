Regression training for [[Neural Nets]]
### Tuning Parameters
To fit our data as best as possible we need to tune our linear weightings. To evaluate how well our model fits the data. **Loss Function** effectively tells us how well the neural network is mapping relative to the data. $$
(x, y) \rightarrow (x, \hat{y})
$$
we want this difference to be as small as possible. $$
\mathcal{L}(\hat{y}, y) = (\hat{y}-y)^2
$$
is a form the loss function called the least squares. If I draw a vertical line at some x, the distribution of the data is naturally a Gaussian. $$
(w_{1}x + b_{1} - y)^2
$$
would be the function we want to minimize by adjusting the weights $w_{1}, b_{1}$ where $w$ is a weight term and $b$ is a bias. This becomes a multivariable function. 

### Stochastic Gradient Decent
We want to find ourselves at a cost function that is at the lowest value. We assume that our cost function is a convex function where we can follow the gradient leads us to a minima of the function. 

We start with a random weight $w$ and make changes in the weight and see the changes in the cost function to map out the cost function and make future guesses in the direction of the negative gradient.
$$
w_{m, \alpha}^{[n]} := w_{m, \alpha}^{[n]} - \alpha \nabla J
$$
where $\alpha$ is a learning rate which determines how large the steps in the gradient decent we should take. Large steps allow for fast learning, but can result in a system oscillating without reaching the minimum. Small steps prevent this from taking so long.

**Forward propagation**: going from a set of predicted outputs $\hat{y}$ from a random set of inputs. From this pass find the cost function of the model. Each time all of the data has been traversed it is an epoch.
**Backwards Pass**:

This form of training never actually converges, it just continues to orbit the global minimum (we would have to make $\alpha$ infinitely small)

### Batch Gradient Decent
Instead of doing a back propagation after each point, go through all of the data and calculate the gradient of the entire process.

Finishes much faster, but is more likely to end up in a local minima.

### Mini Batch Gradient
Best of both worlds: Splits training set into batches and does batch gradient decent and a back propagation. 

We don't really have a way to determine when a global minimum is reached.

### Optimizing the Decent
To prevent oscillations in the decent, we can implement some feedback so that the system has some history.
$$
\alpha = (1 - \beta)\nabla J_{old} + \beta \nabla J_{new}
$$
This adapts our learning rate so that it responds to previous gradients.

##### Hyperparameters
These are the parameters not selected in the training process, but are instead chosen by the trainer.

There are two general approaches: Panda and caviar

The caviar approach is putting combinations of hyperparameters and brute forcing all of the different parameters.

Panda is the total opposite where parameters a hand selected and monitored closely.