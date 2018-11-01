---
layout: post
title:      "Bare Necessities 2.0"
date:       2018-11-01 21:17:42 +0000
permalink:  bare_necessities_2_0
---

## Summary
My most recent project was a refactor of my third portfolio app, Bare Necessities. Bare Necessities 1.0 was a Ruby on Rails, calendar app. The features of the site loosely resemble Google’s calendar app. In this article I will break down the technologies used, challenges faced and learning moments in my second version of the app, Bare Necessities 2.0. 
My app differentiates itself from other portfolio projects because it is not a straightforward content management system. The data structure and user interface are a bit more complicated because we are trying to represent data across an accurate timeline. In my case, the timeline is largely based on the calendar month (the homepage, views, and features center a monthly lense). 

I chose to create a calendar app because I knew that it would challenge my coding skills in new ways. I’ve never created an app where the content generated needs to render in a very specific, orderly fashion. For example, every time we create an event, the data must be placed on the specific calendar day in the browser. That was a brand-new challenge for me. I also knew that practice working with date objects in Ruby would be beneficial. 

Bare Necessities improves in its second version as the content now renders dynamically with the power of JavaScript and a JSON API. In more plain terms, the content renders immediately on the page, without a page reload. Many features of this app remained the same, with the main difference being the subtle differences in the way information is loaded on the page. Submitting information without a page reload ensures the browser doesn’t ‘lock up’ for the user during a page reload, because the page isn’t reloading. This is much more user friendly and gratifying. 

Many features updated followed a similar AJAX workflow. JavaScript allows the browser to ‘listen’ for an event, such as clicking a button or link, or submitting a form. With JavaScript we ‘hijack’ the default action, meaning we intercept data before a page reload occurs. With that data, we then make a request to POST to an API endpoint (change data), or GET (retrieve data) information from the API endpoint. The request routes to our controller actions, interacts with the database, and then sends data back to JavaScript in the form of JSON, or JavaScript Object Notation.  With this data, JavaScript is used to place and update elements of the browser seamlessly. There is no page reload, URL changes, or ‘loading’ as there typically would be if we hadn’t ‘hijacked’ the events mentioned earlier. 

## Features & (technology):

•	Dynamic content rendered without a page reload (JavaScript, JQuery, AJAX, Active Model Serialization JSON Backend) 

•	Login with Google (Omni-Auth, BCrypt)

•	Create an Event, with a title, description, date, start and end time (Ruby on Rails, Object Oriented Programming, ActiveRecord, SQLite Database) 

•	Create a Task related to an Event. A user can create multiple tasks as a to-do list specific for the event. (Ruby on Rails, MVC framework, Object Relational Mapping)

•	The Week Ahead report which lists all events and tasks for the upcoming calendar week

•	Error message generation upon submitting a form with invalid data, preventing bad data from being saved (Active Record Validations) 

## Challenges and What's Next

Most of the challenges faced in this project centered around the configuration and set up. I’ve built an app in Ruby on Rails before, but this was my first time incorporating JavaScript, JQuery, and AJAX. The set up, required in the application manifest, routes.rb file, and incorporating jQuery was challenging. I debugged for a couple hours when my first reference to jQuery triggered an error in the browser. I knew that I was loading jQuery in a variety of different ways. I realized later, that the order on my requirements in the application manifest was wrong, and my JavaScript files were being loaded before jQuery, thus trigger the unknown reference errors. 

I also struggled to wrap my mind around how an AJAX request manipulates data. This was exasperated by a requirement to translate the JSON responses into JavaScript Model Objects using constructor syntax. I think my implementation of this, to meet the project requirement felt a bit contrived, which is perhaps why I struggled with it so much. I understand now that sometimes its advantageous to mirror our ruby object models with JavaScript model objects so that we have greater control over the data we’d like to render in the browser with AJAX. Through JavaScript Model Objects, we can update the database as before, but also customize the amount of data and requests being made to the database. Instead of passing entire ruby objects through the controller, we can simplify the data into a new, slimmer, JavaScript model object. Anything that limits and simplifies data requests will benefit the user. 

I’d like to keep iterating on this project, mostly to add features and improve the CSS, but for now, I will focus on moving through the upcoming curriculum on React and Redux. Thanks for your support. I’ve linked my github repo [here](https://github.com/AubreyNeimeier/bare-necessities-js). The READme.md files contains additional information about my project. I also have a video demo here. Cheers. 







