---
layout: 
title: "Things to know when building your first Rails GraphQL backend(catchier title pending)"
description: >
  Things I learned when setting up GraphQl in Rails
tag: [blog]
---

Hey readers!

![crickets](assets/img/cricket_giphy.gif)

Since the last post, I've been created a GraphQL database with Rails. Here are the steps I took to get started.

1. Start a new rails project with postgresql. Decided against using the --api tag since I wasn't sure of the future of this app and I can always go back and change this setting in the future
~~~
rails new --database=postgresql
~~~

2. Follow instruction for installing the graphql gem [here](https://github.com/rmosolgo/graphql-ruby/) bundle and install

3. Create your Rails schema. In my case, I was making a database of recipes including a users, recipes, and ingredients. Associations and simple validations all set up.

My goal for this exercise was to understand creating the graphql schema, making queries, and making mutations.

## Tip #1 ##
The Graphiql gem is installed once you install graphql (with it's own route no less!) and is awesome tool to use to test out queries and mutations. It even has a nifty catalog of your queries, mutations, and objects on the right-hand panel. Every time I wrote a new query or mutation, I'd test it out in Graphiql.

## Tip #2 ##

A few things about creating queries. Here's a look at my query_type.rb file:

~~~
Types::QueryType = GraphQL::ObjectType.define do
  name "Query"

# simple query looking for all users
# Notice Types::Usertype is in brackets unlike
 the second example since we are querying multiple instances of an object

  field :users, types[Types::UserType] do
    description "All Users"
    resolve ->(obj,arg,ctx) {User.all}
  end

# Query that accepts an argument

    field :who, Types::UserType do
      argument :user_id, !types.String
      description "Look for a user by ID"
      resolve ->(obj,arg,ctx) {User.find(arg[:user_id])}
    end
# For each object, need to run rails g graphql:object [object_name]
    field :recipes, types[Types::RecipeType] do
      description "Recipes"
      resolve ->(obj,arg,ctx) {Recipe.all}
    end
end

~~~
