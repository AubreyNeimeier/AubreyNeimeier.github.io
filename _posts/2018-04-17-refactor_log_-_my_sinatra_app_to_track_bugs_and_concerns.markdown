---
layout: post
title:      "Refactor Log - My Sinatra App to Track Bugs and Concerns. "
date:       2018-04-17 10:53:53 -0400
permalink:  refactor_log_-_my_sinatra_app_to_track_bugs_and_concerns
---

My sinatra app is meaningful in the sense that it solves a problem or pain that people who code experience. As a programmer, we often move forward despite the code not being perfect when we are creating and designing a web app. We strive to take tiny steps forward towards the solution without worrying if the code is perfect. We can always come back and refactor the code once we have it working. The problem we face, is that although we can comment on these peices of code that we plan to refactor later, it isn't ideal. Comments are ugly and are scattered within huge file directories. Finding and remembering where all the code is that needs refactoring is tedious and ineffecient. 

My app is a private, running log of programming projects and their concerns. By concerns I mean any bits of code that are not up to par for one reason or another. Maybe the code isn't DRY, needs further testing, isn't semantic, or the syntax is inconsistent. Essentially, any reason that might bring you back to a section of code for refactoring can be tracked and saved in my app. 

My app holds three models; Users, Projects, and Concerns. Concerns belong to a project and a project has many concerns. Projects belong to a user, and a user has many projects, and also many concerns, through their projects. Upon signing up or logging in, a user can view their projects and concerns. A user can create, read, update and delete their concerns and projects. Validations are in place such that only the owner of the project or concern can modify it's content. 

The web app itself is doing a couple cool things under the hood. It encrypts the password so that nobody (not even the developer) can see the password. The user information, all the projects and concerns are persisting to a SQL database. A user can only edit and modify content that they have created themselves.

I found this project to be very straightforward and easy. The hardest part in face, was coming up with the idea. I knew I wanted an app that solved real world problems as I've noticed some of the best and most recognized ruby gems solve problems. 

Git hub repo: [Git hub repo](https://github.com/AubreyNeimeier/Refactor-Log-Sinatra-CMS-App)
Youtube Video Demo [Youtube Video Demo](https://youtu.be/3-mfMgoI2uk)


