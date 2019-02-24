---
title: "How to take advantage of free GPUs for your ML projects"
categories:
  - machine-learning
tags:
  - machine-learning
  - python
toc: true
toc_label: "Table of Contents"
---

__In this tutorial, we will learn how to take advantage of free GPUs and TPUs to accelerate your Machine Learning projects__

{% include video id="td5ciwor7kI" provider="youtube" %}

The [GitHub links](https://github.com/tuanavu/deep-learning-tutorial) for this tutorial

## Motivation

- To efficiently train a machine learning model on massive amounts of data, data scientists or machine learning engineers often need to use specialized hardware, such as:
    - Graphics Processing Units - GPUs
    - Tensor Processing Units - TPUs
- With these specialized hardwares, the training task that used to take weeks or months to complete now only take minutes. The problem is these hardwares are very expensive, so it requires a huge upfront cost to get started.
- The good news is now you can take advantage of free GPUs and TPUs to develop your machine learning or deep learning models using Google Colaboratory.

## Getting started on Google Colab

- Google Colaboratory is a research tool for machine learning education and research. It’s a Jupyter notebook environment that requires no setup to use.
- It runs on your browser and lets you write, run and share code within Google Drive
- [Tips on using Google Colab](https://medium.com/tensorflow/colab-an-easy-way-to-learn-and-use-tensorflow-d74d1686e309) - medium

## Tips on using Google Colab

1. __TensorFlow is already pre-installed__
	- Just `import tensorflow as tf`, and start coding
2. __Setup your libraries and data dependencies in code cells__
	- Use `!pip install` or `!apt-get` to install extra dependencies. For example: `pandas`, `pytorch`

3. __Integrate with Github__
	- Easy to create a link from Github notebook to Google Colab
	- [Using Google Colab with GitHub](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb#scrollTo=-pVhOfzLx9us)
	- Colab can load public github notebooks directly, with no required authorization step.
	    - For example, consider the notebook at this address: https://github.com/tuanavu/deep-learning-tutorial/blob/master/colab-example-notebooks/colab_github_demo.ipynb.
	    - The direct colab link to this notebook is: https://colab.research.google.com/github/tuanavu/deep-learning-tutorials/blob/master/colab-example-notebooks/colab_github_demo.ipynb.
4. __Share and edit collaboratively__
	- All Colaboratory notebooks are stored in Google Drive. 
	- Colaboratory notebooks can be shared just as you would with Google Docs or Sheets.
5. __Hardware acceleration__
	- By default, Colab notebooks run on CPU.
	- Switch to use GPU or TPU, by going to `Runtime > Change runtime type > Hardware Accelerator > GPU`
	- Google offers a Tesla K80 GPU for the GPU option.
6. __Extra tips__
	- Insert code snippets in Colab
	- Upload your train/test data to Colab
	- Explore [Seedbank project](https://research.google.com/seedbank/): Collection of Interactive Machine Learning Examples

## Ideas on using Google Colab

If you are just getting started on the machine learning journey, here are a few ideas on how you should use it:
- Create a machine learning porfolio on Github, and share it with your future employers.
- Create learning notes for future reference. Example: [data-science-ipython-notebooks](https://github.com/donnemartin/data-science-ipython-notebooks)
- Use Google Colab for reproducible research if you have interesting experiments.
- Share your codes, and work collaboratively with friends and colleages.
- Use Colab for Kaggle competitions.

## Resources
- [Colab: An easy way to learn and use TensorFlow](https://medium.com/tensorflow/colab-an-easy-way-to-learn-and-use-tensorflow-d74d1686e309) - medium
- [Get started with Google Colaboratory](https://youtu.be/inN8seMm7UI) - youtube
- [How to take advantage of GPUs and TPUs for your ML project](https://youtu.be/tCYSce6l8gA) - youtube
- [Using Google Colab with GitHub](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb#scrollTo=-pVhOfzLx9us) - colab notebooks
- [Getting started with PyTorch on Google Colab](https://medium.com/@chsafouane/getting-started-with-pytorch-on-google-colab-811c59a656b6) - medium

