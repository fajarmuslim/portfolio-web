---
date: '2024-07-03T11:50:54.000Z'
title: Recommender System 101 Part 3
tagline: .
preview: >-
  This is the simple implementation to tackle the cold start problem by providing the most popular movies and most highest score movies. Another problem is to recommend what’s next to watch the user based on the last movie that already watched. 
image: >-
  https://images.unsplash.com/photo-1640017955477-75b58521007d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1332&q=80
---

# Real Implementation of Recommender System
This is the simple implementation to tackle the cold start problem by providing the most popular movies and most highest score movies. Another problem is to recommend what’s next to watch the user based on the last movie that already watched. 

![visual representation of the collaborative filtering from wikipedia article](https://github.com/fajarmuslim/recsys-content-based-filtering/raw/main/app/utils/diagram.png)

The example of this implementation of the recsys model is based on [this article](https://towardsdatascience.com/beginners-recommendation-systems-with-python-ee1b08d2efb6) and adapted from the previous article on the Recommender System 101 [Part 2]. 

1. GET most popular movies and GET high score movies
    
    If the new user coming into our platform, the recommendation that are given to them is based on the most popular movies and the highest score movies. The popularity score and movies score already available on the database
    
2. POST retrieve recommendation
    
    The idea is to map the overview text of the movie into vector. To know how much similar of the two vector is calculated from the cosine similarity of the compared those two vector. So, when the user watch the movie X. Then we calculate similarity score between the vector movie X againts all of the movies at our inventory. After that, sort the similarity score to get top N movies that are similar with the movie X. Then, retrieve the movies detail from the database

The detail of code implementation and the guidance is available on [this repo](https://github.com/fajarmuslim/recsys-content-based-filtering) 
