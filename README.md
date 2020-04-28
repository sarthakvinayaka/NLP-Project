# [Deep Learning] IMDB-Movie-reviews-sentiment-classification

This is a mini project in [Deep Learning Nanodegree](https://www.udacity.com/course/deep-learning-nanodegree--nd101) at Udacity. 
Codes including data cleaning the data were provided by Udacity.

In this project, I implemented 2 layer neural network using __Keras__.

## Dataset

The data set contains 50,000 movie reviews from Internet Movie Database (IMDB) labeled whether they are positive or negative.
Each review is preprocessed to be encoded as a sequence of word indexes.
Each word is mapped into an integer that stands for how frequently the word is used.
For instance, let there be a sentence "To be or not to be".
The mapping of the words are as follows:

- to: 5
- be: 8
- or: 21
- not: 3

The above mapping means that 'not' is the top 3rd frequently used word whereas 'or' is the top 21th frequently used word.
The above sentence "To be or not to be" is encoded as `[5, 8, 21, 3, 5, 8]`.

## Data Cleaning

The integers in `[5, 8, 21, 3, 5, 8]` should be treated as categorical variables. 
Which means, I need to prepare the data in one-hot encoding.
The feature set will contain information on whether a specific word is used or not.
To clarify, the vector `[5, 8, 21, 3, 5, 8]` processed into `(0,0,1,0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,1)`.
The processed vectors shows us that 'not' is in the sentence (column 3), 'to' is also in the sentence (column 5) etc.

When constructing the one-hot encoding, I chose the top 1000 frequently used words. Hence, the size of the feature would be 1000.

## Divice the datasets

I first divided the training set and test set in a proportion of 50:50.
Then, I used 80% of the training set when training the model and utilized the remaining 20% as the validation set.

- Training set: 20,000 reviews
- Validation set: 5,000 reviews
- Test set: 25,000 reviews

## Building the model

The model has 2 layers (1 hidden layer) with 128 nodes.
I set dropout rate = 0.5 to prevent the model from overfitting the training set.
I used `relu` for the activation on the hidden layer, and `softmax` on the output layer.
Details are in the `main.py`.
Here's the summary of my model.

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
dense_1 (Dense)              (None, 128)               128128
_________________________________________________________________
dropout_1 (Dropout)          (None, 128)               0
_________________________________________________________________
dense_2 (Dense)              (None, 2)                 258
=================================================================
Total params: 128,386
Trainable params: 128,386
Non-trainable params: 0
```

## Training the model

I trained the model using __Mini-batch gradient descent__ for only 2 epochs with batch size of 100.
Here's result of the training for the two epochs. 

```
Epoch 1/2
20000/20000 [==============================] - 1s 57us/step - loss: 0.4404 - acc: 0.7925 - val_loss: 0.3359 - val_acc: 0.8576
Epoch 2/2
20000/20000 [==============================] - 1s 47us/step - loss: 0.3257 - acc: 0.8600 - val_loss: 0.3294 - val_acc: 0.8568
```

## Testing the model

I tested the model on the remaining 25,000 movie reviews. I got 85.82\% accuracy in prediction.

```
25000/25000 [==============================] - 1s 37us/step
Testing Accuracy: 0.85824
```
