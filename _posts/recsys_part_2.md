---
date: '2024-07-03T11:50:54.000Z'
title: Recommender System 101 Part 2
tagline: This is a Tagline If you want to add.
preview: >-
  we had the movies on demand platform. User use those platform to watch the movies, search the movies, and also can be like, dislike, or bookmark the movies. Each movies there have the data such us the ratings and the popularity. The owner of the platform wants you to help them to increase the revenue, hence they wants their user to spend much more time in their platform. 
image: >-
  https://images.unsplash.com/photo-1656427868828-79a829b92b2b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1332&q=80
---

# Case Overview
we had the movies on demand platform. User use those platform to watch the movies, search the movies, and also can be like, dislike, or bookmark the movies. Each movies there have the data such us the ratings and the popularity. The owner of the platform wants you to help them to increase the revenue, hence they wants their user to spend much more time in their platform. Help the owner to use recommender system to tackle their problem.

# Idea
1. Cold start
    
    The new user supposed to be he didn’t have historical actions such as like, dislike, or bookmark the movies. So, we might didn’t know everything about the user. The solution is to provide the most popular or the high rating movies. Calculation could be:
    
    - The popularity can be calculated based on how many the movie title are searched, watched, and discussed.
    - The high rating of the movies can be calculated to get the average ratings from the users
    
    The considerations: 
    
    - The events of the users to search, watch, give rating, give like / dislike are data intensive events that might occur frequently.
    - Since the events are intensive that required fast data operation on our movies DB. If we directly update the popularity score and average rating, it might required high resource to do that.
    - In another hand, personally I think that the aggregated popularity score for each movies and average rating didn’t changes in fast manner. There could be a trending on movies that long last for a days or weeks.
    
    Hence,
    
    - The calculation should be done periodically to generate those score. The periodic of the generation might the every 1 days and executed at mid night to ensure the server are more available due to low traffic at mid night
    - Then we can “cached” the result into the database table in order to easily retrieved by the user without the need of calculation every the new user comes into our platform
2. What’s next for the user to watch
    
    After user watch X movie. then we can provide the most similar movies with the X movie. The similarity can be calculated based on the properties of the movies such as genre, rating, like / dislike, popularity, etc. 
    
3. User search a movie in our platform 
    
    When user send the query into our platform we can recommend the most similar movie. The method to do this could be:
    
    - search into db directly with query “SELECT * FROM table_name WHERE title like ‘%query%’”
    - to enhance the search capability we might use the capability on postgres DB to do full text search
    - the text search can be more sophisticated using elastic search
    - we can combine the vectorization based of the text to build the text similarity services by comparing the vector of query and the vector of text in our db. There are bunch of the tools to converting from text to vector. e.g: tf-idf, word2vec, BERT, etc.
    
    The problem much more complicated that the user query might have the typo. So, the typo correction can help. There are several python library to do the typo correction
    
    Another enhancement of the search is the autocomplete feature. The autocomplete feature can be achieved using simple mapping and the more advanced approach is use the trie data structure.
    
4. User already had historical data in our platform
If the user already had historical data in our platform, we can leverage the content based filtering, collaborative filtering to tackle this problem. The idea is to recommend the most related movies based on the historical data of the users.