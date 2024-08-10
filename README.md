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

To approximate the 

### Project Presentation Deck:
_Upload/ Link a 3min. presentation deck here._

See project presentation guidelines [here](https://docs.google.com/document/d/13nWF8AxFAfFYTWEYPT3BpPdYkqtxxSAjmuXj_zcMh-E/edit?usp=sharing)

