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

- __[Perceptron](https://en.wikipedia.org/wiki/Perceptron)__    
    - the activation function $$\phi (z)$$ is a simple unit step function, which is sometimes also called the Heaviside step function:

<div class='post image' align='center'>
  <img src='/images/2016-10-22-books-review-python-machine-learning/Screen Shot 2016-10-23 at 8.55.25 PM.png'>
</div>

<div class='post image'>
  <img src='/images/2016-10-22-books-review-python-machine-learning/Screen Shot 2016-10-22 at 9.50.14 PM.png'>
</div>

- __[Adaptive Linear Neuron](https://en.wikipedia.org/wiki/ADALINE)__
    - The key difference between the Adaline rule (also known as the Widrow-Hoff rule) and Rosenblatt's perceptron is that the weights are updated based on a linear activation function rather than a unit step function like in the perceptron. In Adaline, this linear activation function $$\phi (z)$$ is simply the identity function of the net input so that $$\phi(w^Tx)= w^Tx$$.
    - While the linear activation function is used for learning the weights, a quantizer, which is similar to the unit step function that we have seen before, can then be used to predict the class labels.

<div class='post image'>
  <img src='/images/2016-10-22-books-review-python-machine-learning/Screen Shot 2016-10-22 at 9.54.42 PM.png'>
</div>

__Notebooks__:

- [[dir](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch02)] [[ipynb](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch02/ch02.ipynb)] [[nbviewer](http://nbviewer.ipython.org/github/rasbt/python-machine-learning-book/blob/master/code/ch02/ch02.ipynb)]

__Code__:

- [Perceptron](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/perceptron.py)
- [Adaptive linear neurons](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/adaptive_linear_neuron.py)
- [Adaptive with Stochastic Gradient Descent](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch01/adaptive_online_learning.py)

# 3. A Tour of Machine Learning Classifiers Using Scikit-Learn

__Overview__:

- Logistic regression intuition and conditional probabilities
  - odds ratio: which is the odds in favor of a particular event, 

\\[\frac{p}{1 - p}\\], where p stands for the probability of the positive (1− p) event.


  - logit function: the logarithm of the odds ratio (log-odds), 
\\[logit(p) = \log \frac{p}{1 - p}\\]

  

- Learning the weights of the logistic cost function
- Tackling overfitting via regularization
- Large scale machine learning and stochastic gradient descent

__Notebooks__:

- [[dir](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch03)] [[ipynb](https://github.com/rasbt/python-machine-learning-book/tree/master/code/ch03/ch03.ipynb)] [[nbviewer](http://nbviewer.ipython.org/github/rasbt/python-machine-learning-book/blob/master/code/ch03/ch03.ipynb)]

__Code__:

- [Sigmoid activation fuction](https://github.com/tuanavu/machine-learning-ipython-notebooks/blob/master/books/python-machine-learning-book/code/ch02/sigmoid.py)
