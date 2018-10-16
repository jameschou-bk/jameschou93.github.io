---
layout: page
title: "Let's Make a Rails API"
description: >
 Making a simple rails api using jbuilder
tags: [blog]
---

Today we are going to tackle a small API project using Rails that will later be used in a React Js application. We will be using the jbuilder gem in our Rails API to make an awesome looking json view page!

1. **Rails New**
**Let's start** with making our rails app. We are going to specify that we are building an api, omitting any rails middleware that would be useful for a full-blown application like style sheets and cookie support. I am also going to specify that I want use postgre as my database instead of the default sqllite3.

![console]({{ site.baseurl}}/assets/img/2018-02-02-console.png)

2. **Add the jbuilder and faker gem**
The jbuilder gem will allow you to easily create json view pages and keep your code D.R.Y

The faker gem will allow us to seed some fake objects to fill our database with.

Gemfile
~~~ruby
gem 'jbuilder', '~> 2.5'
gem 'faker'
~~~~


3. **Start Your Database**
We will need to generate our models and controllers before create our api. I created a users and business model for this sample.

~~~
rails db:create
~~~
~~~
rails g model user first_name last_name email
~~~
