  ---
layout: post
title: Angular JS intro
tag: [blog]
---

Hey Coders,
These two weeks we are going over the basics of Angular and Javascript. Here’s the crash course:

**Install Angular**
---

I am assuming there are multiple frameworks Angular can be installed into, in my case it is a Rails framework. Here are the steps to installing Rails (sorry everyone else)

1. Go to https://angularjs.org/ and download the uncompressed angular.js file.

2. Copy that file into the vendor/assets/javascripts folder.

3. Add //= require angular to the asset pipeline (i.e. app/assets/javascripts/application.js) on the line before //= require_tree .

4. Get rid of the turbolinks line in that file, which can cause problems down the road.

5. Create a new file inside app/assets/javascripts called app.js.

6. Add the following content to it: https://gist.github.com/jaywengrow/96b28f375e4235b5a70b

7. Back to the application.js: Below require angular, add //=require app (It must be below require angular so Angular can be loaded first.)

8. Add to your HTML. If your browser shows the number 2, congratulations you have angular!: https://gist.github.com/jaywengrow/3e1e2deb0865cd0cca96


**Create your Angular Controller**
---

This controller is going to be similar to your rails controller in the way it is your hub for all javascript functions. You can refer to functions and variables from the controller in your view pages, just like Rails!


Note the differences
---

* Each variable or function begins with $scope.(insert name)


* Referring to variables or functions only requires the name of the function without $scope

* Functions are called in div tags

* Instead of the <%=beehive%> tag for ruby cody, we use {{double curly braces}}

* The each loop is written in the div tag differently than in ruby.


**Ruby**
---

~~~ruby
array.each do |element|
puts element
end
~~~

**Angular**
---

~~~js
<div ng-repeat="elements in array">
{{element}}
</div>
~~~


**BUT MOST OF ALL…**
---

The biggest difference in my opinion is that you can make functions happen with a click or mouse-over!
With angular you can bring your functions to life by adding them to a tag.
![angular post]({{ site.baseurl}}/assets/img/2016-03-15-angularjs.gif)
I hope this helps you all create more interactive applications! Stay tuned.
