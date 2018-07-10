---
layout: post
title:      "Rails Portfolio Project, Bare Necessities"
date:       2018-07-10 13:25:02 -0400
permalink:  rails_portfolio_project_bare_necessities
---

## Summary
My rails portfolio project is a simple calendar (hence the name) with features to add events, and their related tasks. The project is loosely modeled after google's calendar feature. Each user may choose to create their own login, or to login with their google account. 

Upon logging in, the current calendar month is generated with dynamic HTML. I created several helper methods to  properly display the correct date on the correct square in the calendar. My calendar itself is a series of divs, which are generated with a while loop. Every div is given the calendar day as it's content, and a class id which corresponds to that calendar day as well. For example , July 10th, would be generated as:
```

<div class="07-10-2018"> 10 </div>
``` 

The dynamic and unique class id's for each calendar day will become extremely valuable once more features are added. Eventually, I'd like each calendar day to become a clickable button. Upon clicking the specific day, a new event form could pop up, and allow the user to create an event for that day.

## The Stack

This project was written in a ruby on rails framework and makes use of Omniauth for 3rd party verification, bcyrpt for password encryption, rails form helpers, nested routes, validations,  ActiveRecord, and collaborating objects. My three models have the following attributes. 

EVENTS - title, date, date_object, start_time, end_time, description, user_id. 

TASKS - description, event_id, user_id, status

USERS - username, password_digest, provider, uid, oauth_token, oauth_expires_at.


## The Features
Each user has the following features available to them. 
-Login with Google
-Create an Event
-Create a Task related to an Event
- The Week Ahead report which lists all events and tasks for the upcoming calendar week
- Error message generation upon submitting a form with invalid data. 

## Challenges 
One of the reasons I was drawn to create a calendar app was that I knew it would be good practice for working with dates and date objects in ruby.  The event model  has several class methods for queries, and helper methods for generating an accurate calendar month. 

Using omniauth to allow login through google was my second greatest challenge as the set up is entirely new to me. Omniauth removes a bunch of legwork but the logistics are still a bit confusing. I had to register the app and configure settings on Googles API. 



