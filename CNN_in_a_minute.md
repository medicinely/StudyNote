

# CNN in a minute



## Machine learning

You get a set of data that has patterns inherent in it, and we a label to tell computer what those data is. And we have a computer figure out the patterns that match them to each other with the label. Then, my computer will have learned to recognize the data .



## Neural network

The aim of neural network is to figure out the function f with [128] parameters between input image[28x28] and output class[9]

<img src="/Users/StillLoveYou/Library/Application Support/typora-user-images/image-20210128032540226.png" alt="image-20210128032540226" style="zoom: 33%;" />

Set up a model with: input[28x28], parameters[128], output[10]:

```python
model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(128, activation='relu'),
    keras.layers.Dense(10, activation='softmax')
])
```

Set the loss function and optimizer function for our model. The loss function will evaluate the model, and optimizer will generate new parameters for function to see if it can do better:

```python
model.compile(optimizer='adam',
              loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
              metrics=['accuracy'])
```

So simply start training and evaluating:

```python
model.fit(train_images, train_labels, epochs=5)
test_loss, test_acc = model.evaluate(test_images, test_labels)
prediction = model.predict(my_images)
```



## Convolutional neural network

Normal network is boring because it contains the only one feature in the centered of a image. So we carry out the Convolutional neural network.

CNN is a method which filter the images before training the deep neural network. So, features within the images could then come to the forefront and you would then spot those features to identify something.

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gn35dorpblj31vi0u04qp.jpg" alt="image-20210128022300953" style="zoom:33%;" />

For example:

This filter will remove everything except vertical lines

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gn1nd3o45fj31eg0ha1eg.jpg" alt="image-20210126191401730" style="zoom: 33%;" />

This filter removes almost everything except the horizontal lines

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gn1nf2h0r8j31f00gs4k6.jpg" alt="image-20210126191602879" style="zoom:33%;" />

This carry out pooling.

#### Convolutional layer

Our image is fed into the convolutional layer, and we set a number of randomly initialized convolutional kernals(filters) will pass over the image. We can stack convolutional layers on top of each other, and try to learn from very abstract features (*the magic of CNN is the network learns the best filter during training).

And the output of convolution will be fed into the next layer. In each epoch, it will figure out which filters gave the best signals to help match the images to their labels. This process is called feature extraction.



We have a flattened input that's fed into a dense layer that in turn fed into the final dense layer that is our output.

















## Terms

#### Pooling

Pooling is a way to subsample the image, in order to compress the image and enhance the features.

Most common method: Max Pooling (2x2)

<img src="https://tva1.sinaimg.cn/large/008eGmZEgy1gn1nkxlhmvj30ic0aiaat.jpg" alt="image-20210126192143411" style="zoom:50%;" />

#### Loss

A function to calculate how good the guess is.

#### Optimizer

To generate new parameters for the function between input image and output class. The combination of Loss and Optimizer will slowly get us closer to the prediction.

#### Activation function (dense layer)

**ReLU(rectified linear unit):** only keep the value when it's greater than 0

**softmax:** simply set the largest probability to 1 and the rest to 0. What we should do then is to find 1.           

Other: tanh, Sigmoid, 

<img src="/Users/StillLoveYou/Library/Application Support/typora-user-images/image-20210128033854683.png" alt="image-20210128033854683" style="zoom:25%;" />

#### **Muti-Layer Percetion(MLP)**

Add hidden layer to solve non-linear problems, it is the main concept of Neural network.









