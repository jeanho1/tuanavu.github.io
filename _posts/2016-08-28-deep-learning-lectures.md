---
title: "Deep Learning lectures"
categories:
  - deep-learning
tags:
  - python
  - deep-learning
  - machine-learning
  - lectures
---

__This post highlights some great lectures about deep learning__

{% include toc icon="gears" title="Table of Contents" %}

# Stanford CS229

- Only 1 [[slide]](http://cs229.stanford.edu/materials/CS229-DeepLearning.pdf) which gives an intro about deep learning.

# Quoc Le’s Lectures on Deep Learning

- [[Original lectures]](http://www.trivedigaurav.com/blog/quoc-les-lectures-on-deep-learning)
- If you are interested in high level overview of deep learning, these lectures will be a great for your needs. The lectures only have 3 videos of 1 hour each.

> **Update: ** Dr. Le has posted tutorials on this topic: [Part 1](http://cs.stanford.edu/~quocle/tutorial1.pdf) and [Part 2](http://cs.stanford.edu/~quocle/tutorial2.pdf).

[Dr. Quoc Le](http://cs.stanford.edu/~quocle/) from the [Google Brain](http://en.wikipedia.org/wiki/Google_Brain) project team (yes, the one that made [headlines](http://www.nytimes.com/2012/06/26/technology/in-a-big-network-of-computers-evidence-of-machine-learning.html?pagewanted=all&_r=0) for creating a cat recognizer) presented a series of lectures at the [Machine Learning Summer School (MLSS ’14)](http://www.mlss2014.com/) in Pittsburgh this week. This is my favorite lecture series from the event till now and I was glad to be able to attend them.

The good news is that the organizers have made [available](http://www.mlss2014.com/materials.html) the [entire set](https://www.youtube.com/watch?v=4myTpLua0EM&index=1&list=PLZSO_6-bSqHQCIYxE3ycGLXHMjK3XV7Iz) of video lectures in 4K for you to watch. But since Dr. Le did most of them on the board and did not provide any accompanying slides, I decided to put the contents of the lectures along with the videos here.

In this post I posted Dr. Le’s lecture videos and added content links with short descriptions to help you navigate them better.

<table>
    <th>Event Type</th><th>Description</th><th>Course Materials</th>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Neural Networks Review</td>
    <td>
    <a href="https://www.youtube.com/watch?v=IxflKHX7aes&list=PLZSO_6-bSqHQCIYxE3ycGLXHMjK3XV7Iz&index=21">[Video]</a><br>
    <a href="https://github.com/tuanavu/data-science-notebooks/blob/master/deep-learning/quoc-le-lectures/deep-learning-tutorial1.pdf">[deep-learning-tutorial-1]</a><br>    
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>NNs in Practice</td>
    <td>
    <a href="https://www.youtube.com/watch?v=0EM1v6jDD_E&list=PLZSO_6-bSqHQCIYxE3ycGLXHMjK3XV7Iz&index=22">[Video]</a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Deep NN Architectures</td>
    <td>
    <a href="https://www.youtube.com/watch?v=6yHO8pi0GZ8&index=23&list=PLZSO_6-bSqHQCIYxE3ycGLXHMjK3XV7Iz">[Video]</a><br>
    <a href="https://github.com/tuanavu/data-science-notebooks/blob/master/deep-learning/quoc-le-lectures/deep-learning-tutorial2.pdf">[deep-learning-tutorial-2]</a><br>    
    </td>
  </tr>
</tbody>
</table>

# CS231n: Convolutional Neural Networks for Visual Recognition

- This class teaches you how to apply deep learning on Computer Vision. A faily practical class on using Python for machine learning tasks.
- Links:
    - [[Original links]](http://cs231n.stanford.edu/)
    - [[Syllabus]](http://cs231n.stanford.edu/syllabus.html)
    - [[Github]](http://cs231n.github.io/)
    - [[Reddit for discussion]](https://www.reddit.com/r/cs231n)
    - [[Twitter]](https://twitter.com/cs231n)

**Syllabus**

<table>
    <th>Event Type</th><th>Date</th><th>Description</th><th>Course Materials</th>
  <tr>
    <td>Lecture</td>
    <td>Jan 4</td>
    <td>Intro to Computer Vision, historical context.</td>
    <td><a href="slides/winter1516_lecture1.pdf">[slides]</a>
        <a href="https://www.youtube.com/watch?v=NfnWJUyUJYU&index=1&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p"><b>[video]</b></a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 6</td>
    <td>Image classification and the data-driven approach <br> k-nearest neighbor <br> Linear classification I</td>
    <td><a href="slides/winter1516_lecture2.pdf">[slides]</a>
        <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=2"><b>[video]</b></a>
    <br>
    <a href="http://cs231n.github.io/python-numpy-tutorial">[python/numpy tutorial]</a><br>
    <a href="http://cs231n.github.io/classification">[image classification notes]</a><br>
    <a href="http://cs231n.github.io/linear-classify">[linear classification notes]</a><br>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 11</td>
    <td>
     Linear classification II<br>
     Higher-level representations, image features<br>
     Optimization, stochastic gradient descent</td>
    <td>
      <a href="slides/winter1516_lecture3.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=3"><b>[video]</b></a>
      <br>
      <a href="http://cs231n.github.io/linear-classify">[linear classification notes]</a><br>
      <a href="http://cs231n.github.io/optimization-1">[optimization notes]</a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 13</td>
    <td>Backpropagation<br>
     Introduction to neural networks</td>
    <td>
      <a href="slides/winter1516_lecture4.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=4"><b>[video]</b></a>
      <br>
      <a href="http://cs231n.github.io/optimization-2">[backprop notes]</a><br>
      <a href="http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf">[Efficient BackProp]</a> (optional)<br>
      related: <a href="http://colah.github.io/posts/2015-08-Backprop/">[1]</a>, <a href="http://neuralnetworksanddeeplearning.com/chap2.html">[2]</a>, <a href="https://www.youtube.com/watch?v=q0pm3BrIUFo">[3]</a> (optional)
    </td>
  </tr>
  <tr class="info">
    <td>Lecture</td>
    <td>Jan 18</td>
    <td>Holiday; No class.</td>
    <td></td>
  </tr>
  <tr class="warning">
    <td>A1 Due</td>
    <td>Jan 20</td>
    <td>Assignment #1 (kNN/SVM/Softmax/2-Layer Net) Due date</td>
    <td><a href="http://cs231n.github.io/assignments2016/assignment1/">[Assignment #1]</a></td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 20</td>
    <td>Training Neural Networks Part 1<br>
    activation functions, weight initialization, gradient flow, batch normalization<br>
    babysitting the learning process, hyperparameter optimization
    </td>
    <td>
      <a href="slides/winter1516_lecture5.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=5"><b>[video]</b></a>
      <br>
      <a href="http://cs231n.github.io/neural-networks-1/">Neural Nets notes 1</a><br>
      <a href="http://cs231n.github.io/neural-networks-2/">Neural Nets notes 2</a><br>
      <a href="http://cs231n.github.io/neural-networks-3/">Neural Nets notes 3</a><br>
      tips/tricks:
      <a href="http://research.microsoft.com/pubs/192769/tricks-2012.pdf">[1]</a>,
      <a href="http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf">[2]</a>,
      <a href="http://arxiv.org/pdf/1206.5533v2.pdf">[3]</a> (optional)
      <br>
      <a href="http://www.nature.com/nature/journal/v521/n7553/full/nature14539.html">Deep Learning [Nature]</a> (optional)
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 25</td>
    <td>
      Training Neural Networks Part 2: parameter updates, ensembles, dropout<br>
      Convolutional Neural Networks: intro
    </td>
    <td>
      <a href="slides/winter1516_lecture6.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=6"><b>[video]</b></a>
      <br>
      <a href="http://cs231n.github.io/neural-networks-3/">Neural Nets notes 3</a><br>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Jan 27</td>
    <td>
      Convolutional Neural Networks: architectures, convolution / pooling layers<br>
      Case study of ImageNet challenge winning ConvNets
    </td>
    <td>
      <a href="slides/winter1516_lecture7.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=7"><b>[video]</b></a>
      <br>
      <a href="http://cs231n.github.io/convolutional-networks/">ConvNet notes</a><br>
    </td>
  </tr>
  <tr class="warning">
    <td>Proposal due</td>
    <td>Jan 30</td>
    <td>Couse Project Proposal due</td>
    <td><a href="http://cs231n.stanford.edu/project.html">[proposal description]</a></td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 1</td>
    <td>
      ConvNets for spatial localization<br>
      Object detection</td>

    <td>
      <a href="slides/winter1516_lecture8.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=8"><b>[video]</b></a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 3</td>
    <td>
      Understanding and visualizing Convolutional Neural Networks<br>
      Backprop into image: Visualizations, deep dream, artistic style transfer<br>
      Adversarial fooling examples<br>
    </td>
    <td>
      <a href="slides/winter1516_lecture9.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=9"><b>[video]</b></a>
    </td>
  </tr>
  <tr class="warning">
    <td>A2 Due</td>
    <td>Feb 5</td>
    <td>Assignment #2 (Neural Nets) Due date</td>
    <td><a href="http://cs231n.github.io/assignments2016/assignment2/">[Assignment #2]</a></td>
  </tr>
  <tr>  
    <td>Lecture</td>
    <td>Feb 8</td>
    <td>
      Recurrent Neural Networks (RNN), Long Short Term Memory (LSTM)<br>
      RNN language models<br>
      Image captioning
    </td>
    <td>
      <a href="slides/winter1516_lecture10.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=10"><b>[video]</b></a>
      <br>
      <a href="http://www.deeplearningbook.org/contents/rnn.html">DL book RNN chapter</a> (optional)<br>
      <a href="https://gist.github.com/karpathy/d4dee566867f8291f086">min-char-rnn</a>, <a href="https://github.com/karpathy/char-rnn">char-rnn</a>, <a href="https://github.com/karpathy/neuraltalk2">neuraltalk2</a>

    </td>
  </tr>
  <tr class="danger">
    <td>Midterm</td>
    <td>Feb 10</td>
    <td>In-class midterm</td>
    <td></td>
  </tr>
  <tr class="info">
    <td>Lecture</td>
    <td>Feb 15</td>
    <td>Holiday; No class.</td>
    <td></td>
  </tr>
  <tr class="warning">
    <td>Milestone</td>
    <td><b>Feb 17</b></td>
    <td>Course Project Milestone</td>
    <td></td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 17</td>
    <td>
      Training ConvNets in practice<br>
      Data augmentation, transfer learning<br>
      Distributed training, CPU/GPU bottlenecks<br>
      Efficient convolutions<br>
    </td>
    <td>
      <a href="slides/winter1516_lecture11.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=11"><b>[video]</b></a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 22</td>
    <td>
      Overview of Caffe/Torch/Theano/TensorFlow
    </td>
    <td>
      <a href="slides/winter1516_lecture12.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=12"><b>[video]</b></a>
    </td>
  </tr>
  <tr class="warning">
    <td>A3 Due</td>
    <td>Feb 24</td>
    <td>Assignment #3 (ConvNets) Due date</td>
    <td><a href="http://cs231n.github.io/assignments2016/assignment3/">[Assignment #3]</a></td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 24</td>
    <td>
      Segmentation<br>
      Soft attention models<br>
      Spatial transformer networks<br>
    </td>
    <td>
      <a href="slides/winter1516_lecture13.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=13"><b>[video]</b></a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Feb 29</td>
    <td>
      ConvNets for videos<br>
      Unsupervised learning<br>
   </td>
    <td>
      <a href="slides/winter1516_lecture14.pdf">[slides]</a>
      <a href="https://www.youtube.com/watch?v=8inugqHkfvE&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=14"><b>[video]</b></a>
    </td>
  </tr>
  <tr class="info">
    <td>Lecture</td>
    <td>Mar 2</td>
    <td>
      Invited Talk: <a href="https://en.wikipedia.org/wiki/Jeff_Dean_(computer_scientist)">Jeff Dean</a>
    </td><td>
      <a href="https://www.youtube.com/watch?v=T7YkPWpwFD4&list=PLwQyV9I_3POsyBPRNUU_ryNfXzgfkiw2p&index=15"><b>[video]</b></a>
    </td>
  </tr>
  <tr>
    <td>Lecture</td>
    <td>Mar 7</td>
    <td>Student spotlight talks, conclusions</td>
    <td>
      <a href="slides/winter1516_lecture15.pdf">[slides]</a>
    </td>
  </tr>
  <tr class="danger">
    <td>Poster Presentation</td>
    <td>Mar 9</td>
    <td></td>
    <td></td>
  </tr>
  <tr class="warning">
    <td>Final Project Due</td>
    <td><b>Mar 13</b></td>
    <td>Final course project due date</td>
    <td>
      <a href="http://cs231n.stanford.edu/reports2016.html">[reports]</a>
    </td>
  </tr>
</table>
