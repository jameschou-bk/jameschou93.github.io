---
layout: post
title: Intro to debugging
description: >
tags: [hydejack]
---

Hello Readers,
This is my first blogpost about my coding experience. These posts will be for the benefit of my learning process while I am in the [Actualize Coding Bootcamp](http://www.anyonecanlearntocode.com/) and for any coding beginners who may stumble upon my page in the future.
By the time I complete this bootcamp, I will have learned a full stack of languages including Angular, Javascript, Postgre SQL, HTML, CSS, Rails, and Ruby. My classmates and I all began our coding journey by completing novice Ruby and HTML exercises on our own time.


I’ve attached an overview of the subjects that were covered prior to our in-person classes as I believe understanding these rudimentary concepts will make the learning process much smoother in general.

---
1. What is Code?
2. Code Flow (The way your computer reads your code)
3. Values (Strings, Integers, Arrays, Hashes…)
4. Conditionals (If, Else, Elsif, Greater than, Less Than, …)
5. Object Oriented Programming
6. **Debugging**



I would argue that the understanding of these topics as they relate to coding is as important as understanding hammers, nails, and gravity if you were a construction worker.
The reason why debugging was emphasized at the end of my list is because running into an error is inevitable. Being able to read and understand an error message in order to find a solution is invaluable as it can save you a potentially large amount of time, frustration, and hair follicles. Even the simplest of mistakes can produce the most convoluted error message to an unexperienced debugger.


---
~~~ruby
name = 'James'
number_of_cats =
puts 'Hello World my name is' + name + 'I have ' + number_of_cats + 'cats'
~~~~
In the code snippet above, I receive this error:
/Users/JamesChou/Desktop/Actualize/misc/test.rb:4:in `+': no implicit conversion of nil into String (TypeError) from /Users/JamesChou/Desktop/Actualize/misc/test.rb:4:in `<main>'
We can break this error message down into two parts. The first part of the error message is the error path or it’s location. Since code will always read from the top down, the console will always prompt you of the first error it has encountered and which line it has encountered the error. In this case, the error was in line four of my file.
/Users/JamesChou/Desktop/Actualize/misc/test.rb:4:in `+': no implicit conversion of nil into String (TypeError) from /Users/JamesChou/Desktop/Actualize/misc/test.rb:4:in `<main>'
The second half of the message is the cause of the error. Here’s where it can get a bit confusing as error messages are hardly ever in laymen’s terms. For this particular error message, we are looking at the line
~~~ruby
puts 'Hello World my name is' + name + 'I have ' + number_of_cats + 'cats'
~~~
This message is telling us that we cannot add the value “nil” to string, however, we don’t see the word nil anywhere in the sentence we are attempting to create. As a beginner, I was not sure what nil meant which required a quick google search. Then I found out that nil is a placeholder for a lack of value; basically nil equals nothing. This allows me to narrow down the search of my incorrect code to variables, I must have forgot to add a value for either my name or the number_of_cats I have. Sure enough, I did forget to add the number of cats.


---

This was a very simple example of debugging code and the act of debugging becomes progressively more challenging as I learn more complicated syntax and programming. So far Actualize has been a great experience as I am constantly challenged and fortunate enough to enjoy these challenges with like-minded individuals under the instruction of fantastic instructors. I’m confident this will hold true for the rest of the bootcamp as I continue those blogposts!
Happy Coding Everyone!
