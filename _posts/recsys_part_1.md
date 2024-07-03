---
date: '2024-07-03T11:50:54.000Z'
title: Recommender System 101 Part 1
tagline: .
preview: >-
  This series of article devided into three part. Part 1 (this part) will cover what is the recommender system, the usage, and also the approach. Part 2 will cover the design system of the recommender system. Part 3 will cover the implementation of the recommender system and the source code as well.
image: >-
  https://images.unsplash.com/photo-1656188505561-19f1a1b6cda8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1632&q=80
---

# RecSys (Recommender System)
A RecSys is a subclass of information filtering system that provide suggestions for items that are most pertinent to a particular user. Typically, the suggestions refer to various decision-making processes, such as what product to purchase, what music to listen to, or what online news to read. Recommender systems are particularly useful when an individual needs to choose an item from a potentially overwhelming number of items that a service may offer (wikipedia).

### Usage
- Youtube shows us
    - the videos on homepage that might attracted us
    - most relevant videos based on our search
    - videos recommendation after we watch video
- E-commerce shows us
    - most relevant product based on our historical search and activities on their platform
    - most relevant product based on our search query
- etc

# Approach 
### Content based filtering
![visual representation of the collaborative filtering from wikipedia article](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Collaborative_filtering.gif/440px-Collaborative_filtering.gif)
gif source: wikipedia

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Collaborative_filtering.gif/440px-Collaborative_filtering.gif" alt="visual representation of the collaborative filtering from wikipedia article" width="400" height="300">


This approach will return the subset of items from the universe of items based on the most similar items with the specific user preferences. In specific manner we can describe as:

- user had the preferences such as the current search query, historical actions (views, like, dislike), etc
- items had the features such us genre, summary, title, etc
- the goal is to determine the subset of items that most suitable with the user preferences
- the most suitable can be defined as score of how similar the vector user preference and all the vector items. From the similarity score we determine top N items that have highest similarity score.


### Collaborative filtering

The idea of the collaborative filtering is to recommend the item that the users had the similarity on preferences. For example: 

user A likes photography, books, and dislike the games and movies

user B likes photography, books and dislike games. 

intuitively, we can infer that the user B might also dislike movies. 

The user item interaction can be formularize on the matrix where the rows are the user and the columns are the items. The matrix can be grow bigger, so the matrix factorization technique are introduced to handle those condition. The idea between matrix factorization is to compress the matrix into two smaller matrix that the dot product between those two matrix can be constructed into the original matrix. Hence, we have efficient memory to store those matrix.


### Hybrid
Hybrid approach is the combination of the several approach on the recommendation system that aim to fulfill drawbacks on each approach and common problem such as cold start and the sparsity problem
