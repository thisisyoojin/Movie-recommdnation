# Movie Recommendation

## Prepare Data

1. Movie dataframe(item-feature)
It is extracted from the data movie title, relevant links and ratings collected from Wikipedia pages.
I trained the embedding model using relevant links as a connector between titles. With this model, I could get a vectorize matrix of title-features and it was used as an item profile in developing the recommendation system. 

2. Rating(user-item)
This data is randomly generated based on the movie's average rating from the Wikipedia data.


## Evaluation

For evaluation, I used stratified cross-validation and Top-n accuracy. In the group consist of 1 reviewed-item of test data and randomly sampled 100 non-reviewed items, model produce ranked list of recommended items. The model evaluator see whether the interacted item is among the top N items (hit) in the ranked list of 101 recommendations for a user. It computes the Top-N accuracy and Recall for each users and the results will be aggregated for evaluation of the model. 


## Models

1. Collaborative Filtering
This method makes automatic predictions about the interests of a user by collecting preferences or taste information from many users. There are many model-based CF algorithms, like neural networks, bayesian networks, clustering models, and latent factor models, probabilistic latent semantic analysis. 
To build this recommendation system, I used SVD(Singular Value Decomposition). Latent factor models compress user-item matrix into a low-dimensional representation in terms of latent factors. A reduced presentation could be utilized for user-based neighborhood algorithms that are presented in the previous section. 


2. Content-Based Filtering
This method uses information about the features of the items users has previously consumed to model user's preferences. In other words, these algorithms try to recommend items that are similar to those that a user liked or interacted in the past.
At this code, I took items each user rated before and average them to build user preference(user-feature). Based on this user preference, I found item-based neighborhood algorithms to find items with preferred features of the user.


3. Hybrid: 
Hybrid model is combining collaborative filtering and content-based filtering could be more effective than pure approaches in some cases. Aggregate the predictions from Collaborative Filtering and Content-Based Filtering models.


## Result
CF: 'recall@5': 0.3517,'recall@10': 0.5193<br>
CBF: recall@5': 0.05691, 'recall@10': 0.1111 <br>
HYB: 'recall@5': 0.01813, 'recall@10': 0.01813


## Conclusion
As you can see from the result, Collaborative Filtering model is showing the best performance among three models. Content-Based Filtering shows didn't show the good result, which might be related to that the rating data is purely randomly generated and isn't dependent on contents.