## Test your model

Now you've got a working model you can test it using pictures of cats and dogs!

--- task ---

In the last empty cell, add a call to `predict_image` and pass it the URL to a test image.

```python
predict_image('https://dojo.soy/predict-dog')
```

--- /task ---

--- task ---

Try loading a few different images into it to see what predictions it makes. You'll have to use images hosted on the internet. You can use [imagebb](https://imgbb.com/) to put your own images online and then supply the 'direct links' URL to your program. 

![The imagebb link window, with 'direct links' selected and a link URL displayed in the text box below.](images/direct_links.png)

You'll also have to make sure they're `.jpg` files, or modify the `get_image_from_url` function that was supplied with the notebook.

--- /task ---
