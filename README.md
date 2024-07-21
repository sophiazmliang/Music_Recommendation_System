## **Music Recommendation System**

**Capstone Project for the Applied Data Science Program, MIT Professional Education**

Online streaming platforms like Spotify offer millions of songs in their music library. Users often feel overwhelmed by the sheer volume of choices. Developing a recommendation system that suggests relevant songs based on users' historical interactions can significantly enhance user engagement. This increased engagement encourages users to spend more time on the platform, leading to higher user satisfaction and increased subscription renewals or higher advertising revenue from free-tier users, thus improving the platform's overall revenue.

Moreover, such recommendation systems can aid in discovering emerging music trends, guiding strategic decisions on content acquisition, partnerships, and marketing. Continuous improvement and innovation in recommendation algorithms can differentiate a platform from its competitors, establishing leadership in the tech and music streaming industries.

**The objective:**

The primary goal of this analysis is to build a recommendation system that proposes the top 5 songs for a user based on the likelihood of listening to those songs.

This system aims to enhance the user experience by providing personalized content that aligns with individual preferences, allowing users to discover new music they might not have found on their own, thereby enriching their overall experience.

By achieving this goal, the system seeks to increase user engagement, satisfaction, and retention, ultimately driving higher subscription renewals and advertising revenue. Additionally, the system can help management identify emerging music trends and market patterns, enabling strategic decision-making.

**The key questions:**
- What user/song data is available and how can it be used?
- What algorithms and techniques (e.g., collaborative filtering, content-based filtering, hybrid methods) can be used?
- How can user interactions with songs be quantified and used to train the model?
- How to handle data sparsity?
- How to evaluate the recommendation system? What metrics (e.g., precision, recall, F1 score, RMSE) should be used?
- How to address potential biases in the recommendation algorithm to ensure fairness?
- How can the system help identify emerging music trends for strategic decision-making?

**The problem formulation:**
- Data Collection and Preprocessing: Gathering data on user interactions, song features, and metadata. Cleaning and preprocessing this data to make it suitable for analysis.
- Modeling: Using machine learning algorithms (e.g., collaborative filtering, content-based filtering, hybrid models) to predict user preferences.
- Evaluation: Measuring the accuracy and effectiveness of the recommendations using metrics like precision, recall, and RMSE.
- Optimization: Tuning the models to improve performance and scalability.

## **Data Preprocessing**

**We trim down the dataset to only consider:**

1.   users have listened to at least 90 songs (high-engagement user)
2.   songs have been listened by at least 120 users (high-quality music)
3.   play count less than or equal to 5 (excluding outliers which can skew the analysis)


After the trimming process, the dataset has been condensed to encompass **110,000+ user interactions** involving **560+ songs, 230+ artists and 3000+ users**. This refined dataset provides a more manageable and computationally efficient foundation for constructing recommendation systems.

Based on the count of unique users and songs, there exists a potential for 1,776,265 interactions (3155 users * 563 songs) within the dataset. However, the actual recorded interactions amount to only 117,876, representing approximately **6.6%** of the total potential interactions. This discrepancy underscores the reality that not every user has engaged with every song in the dataset, a common occurrence in such datasets.

While this presents an opportunity to develop recommendation systems for suggesting songs that users have yet to interact with, it also introduces **the challenge of data sparsity**. Addressing this challenge will be paramount in ensuring the efficacy and relevance of the recommendation algorithms.

## **Algorithms and models analysis**

In this case study, we built various recommendation systems:
- Popularity-Based
- Similarity-Based Collaborative filtering (user-user and item-item)
- Matrix Factorization Based Collaborative Filtering
- Clustering-based
- Content-based collaborative filtering
- Hybrid (combine SVD, user-user, item-item and Clustering-based, with Linear, Ridge and Lasso regression)
- Hybrid - Random Forest

The surprise library was used to demonstrate all of the Collaborative-filtering-based algorithms. For all of these algorithms, Grid Search Cross-Validation was used to find the optimal hyperparameters for the data, and to improve upon the baseline algorithms. In addition, the optimal hyperparameters were used to generate related predictions.

**Insights:**

- Our dataset contains limited information about the songs and users themselves, necessitating a heavy reliance on user-song interactions to uncover latent features and clustering patterns.

- We face the challenge of data sparsity which is common in recommendation systems.

- Among these techniques, hybrid models generally outperform others in sparse data scenarios by integrating various data sources and methodologies, and leveraging the complementary strengths of different approaches.

- Matrix Factorization models also show strong performance due to their ability to uncover latent factors and generalize well with limited data.

- Content-based and simple collaborative filtering methods may lag behind in sparse datasets due to their reliance on either detailed metadata or sufficient user-item interactions.


## **Proposal for the final solution design:**

*   **Hybrid model which combines SVD and user-user with Ridge regression**

*   It has the **highest F1 score (0.530484)** and **high recall score (0.798430)** among all the models we tried, precision score is close the other models', making it the **best-performing model**.

*   High recall can lead to more engagement, as users find more songs that they enjoy. This is particularly important in competitive markets where retaining user attention is crucial.

*   *Hybrid model which combines SVD, user-user, item-item and Clustering-based model with Lasso regression* maybe the *2nd choice*. As It has the **highest recall score (0.819106)** and **high F1 score (0.525687)** among all the models we tried.
