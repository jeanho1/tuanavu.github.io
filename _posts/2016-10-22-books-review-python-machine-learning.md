---
title: "Book review: Python Machine Learning"
categories:
  - python
  - machine-learning
  - book
tags:
  - python
  - machine-learning
  - book
---

{% include toc icon="gears" title="Table of Contents" %}

- Book: [Python Machine Learning](https://www.amazon.com/Python-Machine-Learning-Sebastian-Raschka/dp/1783555130)
- Author: Sebastian Raschka
- [Github](https://github.com/rasbt/python-machine-learning-book)

# 1. Machine Learning - Giving Computers the Ability to Learn from Data

__Overview__:

Intro to three different types of machine learning:
- Supervised learning
- Unsupervised learning
- Reinforcement learning

__Notebooks__:

- [[dir](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch01)] [[ipynb](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch01/ch01.ipynb)] [[nbviewer](http://nbviewer.ipython.org/github/rasbt/python-machine-learning-book/blob/master/code/ch01/ch01.ipynb)]

# 2. Training Machine Learning Algorithms for Classification

__Overview__:

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

$$
y = -2.2x + 0.5
$$

- __[Perceptron](https://en.wikipedia.org/wiki/Perceptron)__    
    - the activation function $\phi (z)$ is a simple unit step function, which is sometimes also called the Heaviside step function: $
\phi (z) =
\left\{
    \begin{array}\\
        1 & \mbox{if } z \geq 0 \\
        - 1 & \mbox{otherwise }
    \end{array}
\right.
$.

<div class='post image'>
  <img src='/post_images/2016-10-22-books-review-python-machine-learning/Screen Shot 2016-10-22 at 9.50.14 PM.png'>
</div>

- __[Adaptive Linear Neuron](https://en.wikipedia.org/wiki/ADALINE)__
    - The key difference between the Adaline rule (also known as the Widrow-Hoff rule) and Rosenblatt's perceptron is that the weights are updated based on a linear activation function rather than a unit step function like in the perceptron. In Adaline, this linear activation function $\phi (z)$ is simply the identity function of the net input so that $\phi(w^Tx)= w^Tx$.
    - While the linear activation function is used for learning the weights, a quantizer, which is similar to the unit step function that we have seen before, can then be used to predict the class labels.

<div class='post image'>
  <img src='/post_images/2016-10-22-books-review-python-machine-learning/Screen Shot 2016-10-22 at 9.54.42 PM.png'>
</div>

__Notebooks__:

- [[dir](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch02)] [[ipynb](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch02/ch02.ipynb)] [[nbviewer](http://nbviewer.ipython.org/github/rasbt/python-machine-learning-book/blob/master/code/ch02/ch02.ipynb)]

__Code__:

- [Perceptron](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/perceptron.py)
- [Adaptive linear neurons](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/adaptive_linear_neuron.py)
- [Adaptive with Stochastic Gradient Descent](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/adaptive_online_learning.py)

# 3. A Tour of Machine Learning Classifiers Using Scikit-Learn

__Overview__:

- Modeling class probabilities via logistic regression
- Learning the weights of the logistic cost function
- Tackling overfitting via regularization
- Large scale machine learning and stochastic gradient descent

__Notebooks__:

- [[dir](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch03)] [[ipynb](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch03/ch03.ipynb)] [[nbviewer](http://nbviewer.ipython.org/github/rasbt/python-machine-learning-book/blob/master/code/ch03/ch03.ipynb)]

__Code__:

- [Sigmoid activation fuction](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch02/sigmoid.py)
