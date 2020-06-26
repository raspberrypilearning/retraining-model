## Get and split training data

The first thing you'll need to train a model is some data. Models don't learn in the way a human might, by being taught rules. They learn from examples, usually thousands of them, and use those to create their own rules. Some of those rules may be recognising parts and then combining that reognition into a whole, like a human might. For example, if the training data for a cats vs dogs classifer there are no pictures of black dogs, but many of black cats, the model may learn the rule 'black = cat', which will cause problems if you later try to classify pictures of a black dog. So you have to make sure that the full diversity of things the model may eventually be asked to classify is represented. However, for this project, you will be using an existing dataset of cats and dogs that is provided by the TensorFlow library, so someone has already done that work for you.

A Google Colab project has been prepared for you with some starter code. The first thing to do is to open that up and save your own copy to work on.

--- task ---

Open the [Google Colab starter notebook](https://colab.research.google.com/drive/1uKqhEOSu9pIKVwgw4GOHqeq-jzPaYYMH#scrollTo=gebsfn75wKRg){:target="_blank"}  for this project in a new tab in your browser.

--- /task ---

--- task ---

Before you start changing anything, make sure you save the notebook to your drive so you can keep your work! Choose `File > Save a copy in Drive` and sign in to your Google account if prompted.

![The 'File' menu in Google Colab, with 'Save a copy in Drive' highlighted.](images/save_to_drive.png)

--- /task ---

There's already some code, in the second cell, that loads the `cats_vs_dogs` training data. This data is a collection of image files and **labels** for these files, telling the computer which image is of a cat, and which of a dog.

```python
import tensorflow_datasets as tfds
(raw_training, raw_validation, raw_testing), metadata = tfds.load(
    'cats_vs_dogs',
    split=['train[:80%]', 'train[80%:90%]', 'train[90%:]'],
    with_info=True,
    as_supervised=True,
)
```

The data gets broken into three groups, with the percentages defined in the `split` parameter of the load call:

Training data
: This data is used to train the model — to learn rules and decide how important they are.

Validation data
: This data is used to evaluate how well the model is performing while it is being trained. It is checked regularly during the training process. It has to be separate to the training data, or the model might learn only the exact images in the training data, with no general rules for identifying a dog or cat.

Testing data
: This data is not used during the training process, but is used in evaluating how well it performs on unseen data. This check is used to avoid the risk of **overfitting**, where the model learns rules that are specific to the training and validation datasets but do not apply to all cats and dogs.


The data in those three groups needs to be broken into **batches** — groups of images. Each batch gets used to train the model before the model's **weights**, which define how important each rule is, get updated. The bigger the batch, the longer the gap between updates. 

There's no real rule for how big your batches should be, and it may be worth experimenting with different batch sizes on different data, to see if you get better results. Popular sizes are 32, 64, 128, and 256. It is possible to use batches as small as a single image, or as large as your whole dataset. For now, though, you're going to use 32.

--- task ---

In the first blank cell in the notebook, create a `BATCH_SIZE` variable with the value of 32. 

```python
BATCH_SIZE = 32
```

--- /task ---

The use of uppercase letters here is a convention for variables that are manually set by the programmer, but not changed in the course of the program. You could just enter 32 directly where the variable gets used, but this makes it easier to update later.

Each batch is chosen randomly from a **shuffle buffer** of images selected from the full test, validation, or trainng dataset. You have to define the size of this buffer. The bigger it is, the more randomly shuffled your images will be, which is usually a good thing, but the slower the program will run. Again, start by creating a variable for the buffer size.

--- task ---

Below your previous `BATCH_SIZE` variable, add this code:

```python
SHUFFLE_BUFFER_SIZE = 1000
```

--- /task ---

--- task ---
Now that you've set your batch and buffer sizes, you need to break your training, validation, and testing data up into batches. This code will create the shuffle buffers and choose the batches from them. Add it below the two variables you just created.

```python
training_batches = trainig_data.shuffle(SHUFFLE_BUFFER_SIZE).batch(BATCH_SIZE)
validation_batches = validation_data.shuffle(SHUFFLE_BUFFER_SIZE).batch(BATCH_SIZE)
testing_batches = testing_data.shuffle(SHUFFLE_BUFFER_SIZE).batch(BATCH_SIZE)
```


--- /task ---
