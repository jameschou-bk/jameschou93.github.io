---
layout: page
title: "Why GraphQL?"
description: >
  An answer to a question being asked more and more in 2019
tag: [blog]
---

Returning to blogging! Here's why:

- Just attended a tech meetup that made me realize how soft my coding muscles have become
- Reinforcing my learning
- Green squares on Github

So the hot new thing to implement is GraphQl. Lucky for me, the startup I work for has already established a fleshed out GraphQL backend for me to learn from but there's still a good amount of it's utilization that I'm not too savy on.

 Solution: create my own backend so I don't break PHI and our business as a whole.

I had some trouble explaining the benefits GraphQl to a friend the other day so here's what I should've said for future reference:


-  **Efficient Queries**: You can get the info you need with one query rather than ALL the information from a request from a REST API. So instead of parsing through an entire directory of movies, I can do something like this:

~~~
query {
  director(last_name: "Tarantino") {
    name
    movies{
      title
      lead
      year
    }
  }
}
~~~

and get a result like:

~~~
{
  "data": {
    "name": "Quenton Tarantino"
      {
        "title": "Pulp Fiction"
        "lead": "Samuel Jackson"
        "year": "1994"
      }
      {
        "title": "Resrvoir Dogs"
        "lead": "Harvey Kietel"
        "year": "1992"
      }
      {
        "title": "Kill Bill"
        "lead": "Uma Thurman"
        "year": "2003"
      }

  }
}
~~~

- Multiple queries per request! You'll find yourself making fewer requests to your backend, therefore your apps will look and feel snappier!

- You can set aliases for your queries for convenience and, if you need to send a request with multiple queries with different arguments for the same field, you can send the aliases instead.

In conclusion, if anyone asks about GraphQl and you don't feel like opening your mouth, link them to this blogpost.

I'll be playing around with my very own GraphQL database generated in Rails. Updates to come!

GraphQl also has one of the most enjoyable learning/documentation sites I've experienced. If you'd like to learn the basics, look no further than [https://graphql.github.io](https://graphql.github.io)
