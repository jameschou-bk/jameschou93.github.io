---
layout: page
title: "Vote on Rails[Bonus: Vote as a guest!]"
description: >
 Learn to use the act_as_votable gem
tags: [blog]
---

As a fellow Rails developer, you have most likely received the task of creating something similar to a blogging app (bare with me if you haven't). Recently, I have had to create one complete with commenting, sharing, and voting capabilities. Typically I would take time to map out the schema prior to running `rails new` but in this case I was pressed for time. Luckily I had the [`act_as_voteable` gem](https://github.com/ryanto/acts_as_votable) to save the day!

Installation is very basic as all you need to do is include the gem in your gemfile and bundle:


```ruby
gem 'acts_as_votable', '~> 0.11.1'
```


and generate + migrate their migration:

```
rails generate acts_as_votable:migration
rake db:migrate
```


Now let's roll!


My favorite thing about this gem is that the methods to create votes and show votes are simple. First thing we need to do is make the associations between the objects you want to vote on and the voters. In this case, I want to users to vote on my posts. Here is a look at my User.rb and Post.rb files:

user.rb

~~~ruby
  # Voter.
  acts_as_voter
~~~

post.rb

```ruby
  #Votee
  act_as_votable
```


Now that the app knows that users vote on posts, we need to create upvote and downvote methods in our Post controller. The awesome thing is that the gem already limits one vote per user(default but can allow duplicates) and you can also make vote weighted based on user role if you wanted! I did not use weighted votes in my app but if you want learn more about how else you can play around with voting, definitely look at the great documentation that [ryanto has for his gem!](https://github.com/ryanto/acts_as_votable)


Post Controller

```ruby
def upvote
    @post = Post.find(params[:id])
    @post.liked_by current_user
    #can change current_user to any other voter
end

def downvote
    @post = Post.find(params[:id])
    @post.disliked_by current_user
    #can change current_user to any other voter
end
```

and in my html view:

```ruby
<%= link_to "Like", like_post_path(@post, method: :put) %>
```


What you have read so far is a barebones quick install tutorial and there is definitely potential for further manipulation of votes. [See Documentation!](https://github.com/ryanto/acts_as_votable). But I did find myself in an issue...what if I want guests to vote?!


Through extensive research from various sources(google,stackoverflow,my sensai, etc) I found a way to do this with session ids!

This time, we have to allow users AND sessions to act as voters; we need to add `act_as_voter` in both of the votersession.rb and user.rb files. But first we need to generate a votersession model.


```ruby
rails g migration votersessions session_id:string
rails db:migrate
```

and now we simple need to change our controller to use the User object to vote and, if not available, the session id instead. Here's my moist(not [DRY](http://wiki.c2.com/?DontRepeatYourself))

```ruby
  def upvote
    @idea = Idea.find(params[:id])
    # vote as user if logged in
    if current_user
      @idea.upvote_by current_user
    # else vote is associate with session
    else
      @session = VoterSession.find_by(session_id: request.session_options[:id])
    # Create new votersession if unique id does not exist
        if @session == nil
          @session = VoterSession.create(session_id: request.session_options[:id])
        end
      @idea.upvote_by @session
    end

```

Keep in mind, there is still a chance for voters to vote more than once, for example, if the user is not logged in, they can vote again each time they clear their cookies or use a different computer so I recommend this method for smaller apps that need a quick voting structure.

My hope is that this post can be of use to a dev out there or at the very least sparked an idea. Drop a line if you have any questions!
