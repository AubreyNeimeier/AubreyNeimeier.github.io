---
layout: post
title:      "How do ActiveRecord and Sinatra Work Together? "
date:       2018-03-30 12:17:09 +0000
permalink:  how_do_activerecord_and_sinatra_work_together
---

Sinatra is a framework to help you control flow and implement actions for a website.  

They tie together mostly through the creation of objects (users, cats, teachers, songs...pick any example you like) and also through web forms. 

For example. Pretend you are signing up for a website. You complete a form that asks for a username and a password. To persist their information so the user can login later, we need to create an User object and save it to the database. 

Sinatra will capture what was entered in the web form, route that data to a specific action, which will manipulate or create a relevant object and/or render a new web page. Sinatra is you your map between URL’s, user actions and the next steps for the website. ActiveRecord provides convenience for creating and deleting objects/ updating objects in our database within those actions. 


