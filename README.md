# project

Classify movie review in negative and positive category.

# Description
This notebook classifies movie reviews as positive or negative using the text of the review. This is an example of binary—or two-class—classification, an important and widely applicable kind of machine learning problem.
We'll use the IMDB dataset that contains the text of 50,000 movie reviews from the Internet Movie Database. These are split into 25,000 reviews for training and 25,000 reviews for testing. The training and testing sets are balanced, meaning they contain an equal number of positive and negative reviews.

# Data
The IMDB dataset is available on imdb reviews or on TensorFlow datasets. The following code downloads the IMDB dataset to your machine (or the colab runtime) with 25000 training and 25000 testing labels. Each example is a sentence representing the movie review and a corresponding label. The sentence is not preprocessed in any way. The label is an integer value of either 0 or 1, where 0 is a negative review, and 1 is a positive review.

# Algorithm
We have implied LSTM ( Type of RNN ) in IMDB datasets using Tensorflow and keras that will help to find the review is positive or negative.

Rest detail are commented in code which will help you to understand more clearly.
