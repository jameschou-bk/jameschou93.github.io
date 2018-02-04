---
layout: post
title: Postgres SQL and SQL Queries
description:
image: /assets/img/caleb-george.jpg
hide_image: true
tags: [blog]
---

It has been a couple of weeks since my last post and my mind is bloated with new information from this bootcamp. The topic that I was most excited about this time is Structured Query Language(SQL). There are many types of SQL databases including, SQL lite, MySQL, and Oracle SQL to a name a few. Each of these database types have different features, however, they all use SQL to retrieve data. In this post, I will be referring to Postgre SQL


**SQL Query Structure**
Below I have a dummy database with an extensive list of fake employees and their information.
![dummy database]({{ site.baseurl }}/assets/img/2016-02-2-SQL.png)
I want to find all male employees who are over the age of 50 so that I can send them reminders to schedule their annual prostate exam. Most managers who care about their employees’ health still probably would not want to go through the trouble of sift through each individual piece of data to send out a simple email. This is where SQL comes in!
Here is the general structure of a SQL query:
~~~
SELECT (Columns you would like to see)
FROM (Table you are requesting data from)
WHERE (Conditions the data must meet to appear in your results)
;  <---semicolon states the end of your query
~~~
In my example, I would like to see all the information for my 50+ year old males so I would input:
~~~
SELECT * FROM employees WHERE birth_date < 1967-01-31
~~~
![sql *]({{ site.baseurl }}/assets/img/2016-02-2-SQL.gif)
Using * in my select command will return all columns in the database for my results.
We can also query data based on partial segments of string. For example, if I wanted to find the employee numbers on all employees with a last name beginning in the letter “Z” I can use the query:
~~~
SELECT emp_no, last_name FROM employees WHERE last_name LIKE 'Z%'
~~~
The combination of the LIKE statement and the % symbol allows us to find clients with this partial string. The % symbol tells the system that any value can exist after the letter “Z”. This query can also return all last names that end in “Z” if we entered:
~~~
SELECT emp_no, last_name FROM employees WHERE last_name LIKE '%z'
~~~
Or if we want all last names that contain the letter “Z”
~~~
SELECT emp_no, last_name FROM employees WHERE last_name ILIKE '%z%'
~~~
Notice that for my last query I used ILIKE instead of LIKE which tells the query to become case insensitive.
SQL is a fantastic skill not only for programmers but also for those in healthcare, business, and all professions that deal with big data and there is still much to learn before this language is mastered.
I hope this post was helpful to someone!
