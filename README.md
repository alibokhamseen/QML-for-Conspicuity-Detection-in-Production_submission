# QML-for-Conspicuity-Detection-in-Production
Womanium Quantum+AI 2024 Project


## Project Information:

### Team Information:
Team Member 1:
 - Full Name: Ali Bo Khamseen
 - Womanium Program Enrollment ID (see Welcome Email, format- WQ24-YVXz6oxRxiuP5vJ):


### Project Solution:
_Include a comprehensive summary of all important information about your project solution here._
My submission answers three tasks:
## 1) variational classifiers (2 models)
Here, I present variational models to solve two problems:
### - partity checks

This is a rather simple model where I follow [Pennylane's tutorial](https://pennylane.ai/qml/demos/tutorial_variational_classifier/) to create a model with 100% accuracy.
  
### - Breast Cancer Wisconsin 
[dataset](https://archive.ics.uci.edu/dataset/15/breast+cancer+wisconsin+original)

This dataset includes 9 features, all of which are integers {1, 2, ..., 10\}.  To encode the data, I 
use `AmplitudeEmbedding`, which is provided by Pennylane to automatically initialize my state given a 
state vector. I use 4 qubits as I utilize 10 orthogonal states in my system's Hilbert space. The 10 states 
are represented by 9 features + the magnitude of all 9 features. The magnitude value is needed to preserve 
information about the vector's length after normalization. 

The model achieves 97% accuracy on training data and 95% on the validation set. You can visit the [dataset](https://archive.ics.uci.edu/dataset/15/breast+cancer+wisconsin+original) 
to compare my results with classical models.

At the end, I note that even though I optimize my model to do rotations on three Pauli directions (X, Y, Z), 
the final model only needs Y rotations. 


## 2) Quanvolution
I followed [Pennylane's tutorial](https://pennylane.ai/qml/demos/tutorial_variational_classifier/) 
to construct classical neural network with input processed using a quantum layer. Final results show that the quantum layer doesn't 
add any advantage over a fully classical model when used with the MNIST fashion dataset. Also, adding more random 
quantum layers produced worse results. I expect this happened because adding random layers prodcues randomized results with 
less apparent patterns to classical models.


## 3) Sin function approximation

I present two models. 

### - Encode the solution in a single qubit expectation value

This methode trains a model using a `precision` parameter. The advantage of this model is that it only needs a single qubit, but the downside is that using the model in real life requires many shots to get expectation value within the desired precision. 

This model is easy to train and doesn't require large training set for `precision = 0.001` (I used 100 data points). This model achieved 100% accuracy on unseen data.

### - Binary fraction extraction $-$ multi qubit

For this model, I attempt to find the first `n` binary fractional bits of the solution. 

$\sin(x) = \alpha$, where in binary $\alpha = a_0 . a_1a_2...a_n$

$$\alpha = a_0 \cdot 2^0 + a_1 \cdot 2^{-1} + a_2 \cdot 2^{-2} + \dots + a_n \cdot 2^{-n}$$

where $a_i \in \\{0, 1\\}$


I first convert the input into binary. Note that my conversion isn't about finding the ideal approximation but about taking the first `n` binary fractional bits. This method takes decimal inputs and converts them to binary, whose accuracy depends on the parameter `n`. The binary input encoding into the quantum circuit allocates a qubit for the sign, a qubit for the integer part of the binary number, and `n` qubits to represent each fractional bit.

To get the labels using the binary representation of the input:

binary input -> decimal input -> sine() -> decimal label -> binary label

For `n = 3` the model achieved 100% accuracy on validation data. It is possible to increase `n` to get higher accuracy. I believe this technique has potential to scale with higher `n` given access to quantum computers.

