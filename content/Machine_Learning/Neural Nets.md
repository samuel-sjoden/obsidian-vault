Our models try to match data. We usually observe experiments, collect data, and then create models that create data.

This means that our models of the world are limited by the data we measure and access.

Neural nets operate in the same way that we develop our own models. It adjusts itself to map to the data it is given. Modern neural networks are working on generating equations that describe the physical data given.

### Image Processing

Moving on from artesinal methods, deep neural networks are being used now for computer vision.

### Our Agents
The neural network will be in a loop with the robot where data is fed into the robot and the neural network responds with control commands.

The amount of processing done by the neural network depends on the scale of the neural network. Instead of prepossessing the data before feeding it into the network and getting the data out in a form to go to a controller. This is much more difficult (more data) but more robust. Need lots of data to feedback into the neural network for it to properly map inputs to outputs (ex. controlling a motor -> need speed, current, load given an input)

### Deep Learning

Deep learning models are the most modern form of neural networks. They levied high processing power from GPU's and a large source of digitized data. Deep neural networks indicate that there are many hidden layers. They can map complex functions much easier.
**Deep vs Shallow**
Additional depth allows us to compress data and patterns, something that would require an exponential amount of neurons for a shallow neural network.
You can run mappings through more passes with greater depth.

More parameters requires more data. Deep neural networks require relatively less data and training time. Deep neural networks have less parameters.


Large enough neural networks are able to generalize to data that are outside of their training set. 

*If all of the neural networks are trained on the same data, are all models eventually converge on being the same?*
#### Nomenclature

Each computing unit (neurons) are connected to other neuron. We define the connections.

Data coming in: Input features
$X \rightarrow \hat{Y}$
The amount of stages between input features and output are called the hidden layers.

#### Neuron Function
Each neuron stores their own weights $w[n]$
The forward pass does a linear transform to the input data, then a non-linear mapping to be able to map non-linear functions

*Why cant we just use local linearizations?*

Because a composition of linear functions will always be another linear function

The activation function (the non-linear mapping). We want it to be monotonic, and continuously differentiable. This is often ReLu(x) $$
\text{ReLu(x)} = 
\begin{cases}
0 &  x \leq 0 \\
x & x > 0
\end{cases}
$$
Neuron takes inputs (a vector) then performs linear transform. Then applies activation function to the transformed data (the bias term).

*is the bias addition from the non-linear term? is not a transform?*

Bias term comes from the linear transform.

*Is each combination of outputs a sum?*

Given an arbitrarily large neural network, you can map any function with arbitrary precision, just like interpolation and Fourier series.

## Three types of learning problems
Supervised, Reinforcement, and Unsupervised

Supervised -> labelled data 
Reinforcement Learning -> gives a high level goal, the neural network figures out which data is valuable and weights it
Unsupervised Learning -> Only giving constraints, input data tries to match output data (model building)

### The Last Layer

The activation function of the final neuron in the network needs to be selected based on the type of problem that the neural network is used for. 

>[!question]
>Why is the SOFTMAX activation node an exponential and not just the raw data


