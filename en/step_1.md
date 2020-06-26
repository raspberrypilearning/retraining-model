## Introduction

### What is a machine learning model?

A model is a set of rules a computer follows to complete a machine learning task, like determining what is in a picture it's shown.

These rules are divided up into **layers**. Each layer looks at the results of the one before it and tests them against some rules to decide what results to pass to the next layer.

![A single black circle connected by arrows to each circle in a column of three pink circles. Each of those circles is in turn connected by arrows to both circles in a column of two pink circles, each of which is connected by arrows to all of the circles in a column of four pink circles. Finally, those four circles are connected by arrows to two green circles.](images/neural_network_diagram.png)

Within each layer there are nodes, which have each learned a rule while the model was being trained, and will test it and produce a result when the model is predicting.

The very first layer is the input to the model — an image in this case. The first layer is often called the input layer for this reason. The last, or output, layer of a classifier model like this will always have a number of nodes equal to the number of classifications the model is trained to identify. For example, in the model you will be creating there will be two nodes in the final layer, as it will be classifying its inputs into either pictures of dogs, or pictures of cats.

### What you will make

You will take an existing model trained to recognise images and retrain it to determine whether pictures show dogs or cats.

You will also create code to measure how well the model can do this, and to show how much you've improved on the original model in this task.

--- collapse ---
---
title: What you should already know
---
This project assumes you already know some Python. Specifically, it assumes you know how to use:

+ Variables
+ Lists
+ Functions, including creating your own function that accepts arguments

It also assumes that you know the basics of how to interact with an image classifying model and get a prediction from it. If you don't, you can learn this in the [testing your compueter's vision project](https://projects.raspberrypi.org/en/projects/testing-vision).

--- /collapse ---

--- collapse ---
---
title: What you will need
---

+ A computer
+ An internet connection
+ A Google account

--- /collapse ---

--- collapse ---
---
title: What you will learn
---

+ What machine learning models are made of
+ How models are trained
+ How to measure how well a model works

--- /collapse ---

--- collapse ---
---
title: Additional information for educators
---

If you need to print this project, please use the [printer-friendly version](https://projects.raspberrypi.org/en/projects/retraining-model/print){:target="_blank"}.

[Here is a link to the resources for this project](http://rpf.io/retraining-model-go).

--- /collapse ---
