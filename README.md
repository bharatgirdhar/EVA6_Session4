# Assignment 4

## Part 1

The excel sheet contains an example to train a deep neural network in excel. There are 2 major parts in it -

1. Forward Propagation
2. Backward Propagation

### Forward Propagation

We have an input of dimenisonality 2 which is fed to the network. The inputs are denoted by `x1` and `x2`.

The network consists of an input layers, a hidden layers, and an output layer. Each layer is followed by an activation function to introduce non-linearity into the network.

- Input: `x1, x2`
- output: `t1, t2`
- Weights: `w1, w2, w3, w4, w5, w6, w7, w8`
- Intermediate outputs: `h1, a_h1, o1, o2`
- Final Output: `a_o1, a_o2`
- MSE Loss: `E1, E2`

Although the parameters are initialised randomly, for our exercise we choose the following values.

| w1  | w2  |  w3  | w4  | w5  |  w6  | w7  |  w8  |
| :-: | :-: | :--: | :-: | :-: | :--: | :-: | :--: |
| 0.3 | 0.5 | -0.2 | 0.7 | 0.1 | -0.6 | 0.3 | -0.9 |

The inputs `x1` and `x2` are used to calculate the neuron values of the hidden layer using the following equation.

`h1 = (w1 * x1) + (w2 * x2)`

`h2 = (w3 * x1) + (w4 * x2)`

These outputs are then passed through a sigmoid function.

`a_h1 = σ(h1) = 1/(1 + exp(-h1))`

`a_h2 = σ(h2) = 1/(1 + exp(-h2))`

Once we have the middle neurons, we then calculate the output neurons using the following equations.

`o1 (w5 * a_h1) * (w6 * a_h2)`

`o2 (w7 * a_h1) * (w8 * a_h2)`

Activations of these outputs.

`a_o1 = σ(o1) = 1/(1 + exp(-o1))`

`a_o2 = σ(o2) = 1/(1 + exp(-o2))`

Once we have the output from the network, we calculate the Mean Squared Error loss using our actual outputs.

`E1 = 0.5 * (t1 - a_o1)²`

`E2 = 0.5 * (t2 - a_o2)²`

Finally, we calculate the total loss using which we'll perform backpropagation.

`E_Total E1 + E2`

### Backward Propagation

During backpropagation, we first calculate the derivative of the total error with respect to all the weights using chain rule.

The final equations are:

`∂E_Total/∂w8 = (a_o2 - t2) * a_o2 * (1 - a_o2) * a_h2`

`∂E_Total/∂w7 = (a_o2 - t2) * a_o2 * (1 - a_o2) * a_h1`

`∂E_Total/∂w6 = (a_o1 - t1) * a_o1 * (1 - a_o1) * a_h2`

`∂E_Total/∂w5 = (a_o1 - t1) * a_o1 * (1 - a_o1) * a_h1`

`∂E_Total/∂w4 = [(a_o1 - t1) * a_o1 * (1 - a_o1) * w6 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w8] * a_h2 * (1 - a_h2) * x2`

`∂E_Total/∂w3 = [(a_o1 - t1) * a_o1 * (1 - a_o1) * w6 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w8] * a_h2 * (1 - a_h2) * x1`

`∂E_Total/∂w2 = [(a_o1 - t1) * a_o1 * (1 - a_o1) * w5 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w7] * a_h1 * (1 - a_h1) * x2`

`∂E_Total/∂w1 = [(a_o1 - t1) * a_o1 * (1 - a_o1) * w5 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w7] * a_h1 * (1 - a_h1) * x1`

Once we the gradients, we update the weights using the following equation.

`w_new = w_old - (LR * ∂E/∂w)`

`LR` is the learning rate which is used to ensure the update step aren't too large. If the LR is too big, the network may not converge at all.

### Learning Rate Experiment

Increasing the learning leads to faster convergence in 100 epochs. The total error reduces quickly for a higher learning rate.

- LR = 0.1
  ![LearningRate=0.1](./Assignment1/0.1..PNG)

- LR = 0.2
  ![LearningRate=0.2](./Assignment1/0.2..PNG)

- LR = 0.5
  ![LearningRate=0.3](./Assignment1/0.5..PNG)

- LR = 0.8
  ![LearningRate=0.4](./Assignment1/0.8..PNG)

- LR = 1.0
  ![LearningRate=0.5](./Assignment1/1..PNG)

- LR = 2.0
  ![LearningRate=0.6](./Assignment1/2..PNG)

### Screenshot

The excel sheet is present in `./Assignment1/Training_NN_Excel.xlsx`. Here's a screenshot of the file.

![backprop](./Assignment1/Details.PNG)

## Part 2

The notebook is saved in the main folder EVA6_Session_4_Assignment2.ipynb

### Test Accuracy: `99.33%`.

## Model Architecture :
![Model Architecture](./Assignment1/Model_Architecture.PNG)

## Training - EPOCS

### Intermediate EPOCS
![Intermediate EPOCS](./Assignment1/Intermediate_EPOC.PNG)


### FINAL EPOC
![Final EPOC](./Assignment1/Final_EPOC.PNG)

