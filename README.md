
Slides:

https://docs.google.com/presentation/d/1J3x_i2OKqbjhE43rMDcc3XrH3QupxnWm_VUh3pgTdt0/edit#slide=id.g6fe2623042_0_6



### Goals structure:
- 10 minutes describing the goal and giving some tips
- 30 minutes of trainees attempting to solve it
- 10 minutes of sharing the solution
- 10 minutes rest

---
# High reads and low write pattern

Iteration 1 
===========

In this stage, we'll start the development of a second function that will take care of materializing the "timeline" of a user, whenever a post creation happens. In order to simplify the exercise let's assume that a user's posts list will be under `posts` table, whereas timeline will be a collection of `posts` from multiple users, which corresponds with the users a user follows. The list of followers will be in another table. 


Goal 1
=======

Have a lambda set to track who is following who (POST follower, GET followers)

Goal 2
=======

Have a new function that holds a wall database and gets triggered by the last sessions (events) post publishing lambda, we will do a fake implementation at the moment: every post that is published is added to every wall regardless who follows who

Goal 3
========
As a fake and not recommended implementation lets call the followers endpoint from the lambda that updates the wall, we shall only update the walls of users that follow the publisher of the post.

Goal 4
========
Lets fix the infrastructure costs for this set up, either you can connect the wall lambda to followers or try to make a call from wall to followers in a asyncronous way with step functions and serverless 


### Tips

The suggested logic includes: 
- User **A** creates a post
- Query the list of users following user **A**
- As user **A** updated his posts list, the users following user **A** should have their timeline updated
- Timeline update will happen simply as adding the same post to each of the followers of **A**


