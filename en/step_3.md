## Prepare the model for retraining

Instead of training a whole new model, you'll be loading an existing one, called MobileNetV2, and changing what it classifies. The big advantage of this is that the model already knows how to identify interesting features of an image. You just need to remove the final layer, where it decides what classes those features match with, and train a new one of your own on the cats and dogs data.

--- task ---

First, define the size of the images you're going to be using. The dataset that you've imported is made up of 160x160 pixel images and, because it's needed in some of the code that came in the notebook, that value is already stored in an `IMAGE_SIZE` variable. So you can reuse it when defining the image shape here. However, because of how colour works on computers, the images are actually three sets of 160x160 pixels — one each of the red, blue, and green values that combine to form the colour displayed at any given pixel. You can see more details on this below, if you're interested.

In the next empty cell, create an `IMAGE_SHAPE` variable:

```python3
IMAGE_SHAPE = (IMAGE_SIZE, IMAGE_SIZE, 3)
```

--- /task ---

[[[generic-theory-colours]]]v

--- task ---
Now, below your `IMAGE_SHAPE` variable, import the MobileNetV2 model — which is trained to identify loads of different objects — pass it your `IMAGE_SHAPE` as its `input_shape` and store it in an `original_model` variable.

```python
original_model = tf.keras.applications.MobileNetV2(input_shape=IMAGE_SHAPE)
```
--- /task ---

Since MobileNetV2 is designed to run on a mobile device with limited battery, like a phone, it's not as large or as powerful as some other models. This means it doesn't always make the best guesses. Before you start changing it, test how good it is by asking it to identify a photo of a dog. Functions to let you do this easily have already been included in the notebook, but to understand how they work, cheack out the [Testing your computer's vision project](#).

--- task ---
Below the model import, add this line:

```python
predict_imagenet('https://dojo.soy/predict-dog')
```

--- /task ---

--- task ---
Now run all the code and see how good the model's predictions are!

You can run all the code by opening the `Runtime` menu and choosing `Run all`.
--- /task ---

![The 'File' menu in Google Colab, with 'Save a copy in Drive' highlighted.](images/dog_prediction_original.png)

There are a couple of dog breeds in there, but most of the model's perferred classifications aren't very good! That's why you're going to improve it!

--- task ---
Remove the call to `predict_imagenet`, you only needed it for testing.
--- /task ---

You need to remove the top layer from the existing MobileNetV2 model, where it decides which of the many objects it's been trained to identify is in the image, so you can add your own layers related to cats and dogs. This can be done when loading the model.

--- task ---
Update the line where you load the `original_model` to add the `include_top` parameter and set it to false.

```python
original_model = tf.keras.applications.MobileNetV2(input_shape=IMAGE_SHAPE, include_top=False)
```
--- /task ---

Finally, because you don't want to change anything in the original model, you should set it to be untrainable.

--- task ---

Below the line where you create `original_model`, set its `trainable` property to false.

```python
original_model.trainable = False
```

--- /task ---
