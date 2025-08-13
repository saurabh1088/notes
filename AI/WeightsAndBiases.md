# Weights & Biases


## What are weights and biases?
Weights and biases are the fundamental learnable parameters of a machine learning model, such as a neural network. They are the numerical values that the model adjusts during training to transform input data into a meaningful output.


## An Intuitive Analogy

Consider a single-person committee tasked with deciding whether a new movie is good. The decision is based on three key inputs (features):

1. The movie's rating on Rotten Tomatoes.
2. The length of the movie.
3. The number of awards won by the lead actor.

Each input is assigned a weight, indicating its level of importance in the decision. For example, the Rotten Tomatoes rating might carry a high weight, the movie's length a moderate weight, and the actor’s awards a low or even negligible weight. These weights determine the degree of influence each factor has on the final judgment.

Alongside these weights is a bias—an inherent predisposition that exists before any inputs are considered. For instance, a natural liking for the movie’s genre might provide an initial positive baseline score. This bias serves as a constant value that can influence the outcome even when all input values are zero, or simply shift the overall score upward or downward.

In this analogy, the final “decision score” is calculated as the weighted sum of all inputs plus the bias. The process of “learning” involves gradually adjusting these weights and biases, based on accumulated experience and data, to arrive at more accurate decisions over time.

Final Decision Score = Σ (feature × weight) + bias

Learning is the iterative process of tuning these weights and biases using training data to minimize prediction error.