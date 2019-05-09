---
layout: post
title:      "Synchronous and Asychronous JavaScript, and Fetch Requests"
date:       2019-05-09 20:53:44 +0000
permalink:  synchronous_and_asychronous_javascript_and_fetch_requests
---


Let’s start with the basics. Generally speaking, JavaScript is single threaded, meaning everything else in the subsequent code is blocked until the current task is completed. Essentially, each operation occurs in order, one after another.  We call this work flow synchronous. Most operations in javascript are performed synchronously. However, there are some disadvantages to synchronous code. Because each action is ‘blocking’, the DOM is paused/frozen or unavailable until the task is complete, leaving the user waiting on a locked browser to open up. If we need to load a bunch of data, the browser may lock up for an unreasonable amount of time while the data is loading. This is unpleasant for the user! 

We want the user to continue to interact and view the page while the data is loading in the background. In order to make this happen, we can use asynchronous code! Asynchronous is the opposite of synchronous - your code continues to run while a time consuming task in being run in the background! Before we move on, let's summarize what we’ve learned so far. 

Synchronous - code is executed in sequence, blocking each subsequent statement from executing until the current one is finished. 

Asynchronous - code executes on multiple threads, meaning many tasks can be completed at once. The order of invocation is sequential, but each task is non blocking so as soon as one tasks begins, the next can start, reducing wait time for the user. 

Web requests in JavaScript are Asynchronous! When we request data from an API, the code following will start running BEFORE the web requests resolves. When the web request resolves we say the promise has resolved. Read more about promises here. This can pose a problem because often we want to manipulate or send the received data in the following code, and if the code is processed before we receive the data, we will run into serious problems! For example, 



![(https://drive.google.com/file/d/1Q7GT8DvR4d-pV03aKy_PUmF8ZkGSvI7C/view?usp=sharing)]
The action creator of type ‘FETCH_DOGS’ would be dispatched before the response is received. To resolve this problem we can chain a .then() function onto the request, so that our action is not dispatched until we receive our data. Additionally another standard practice is to incorporate Redux Thunk middleware, which allows us to return a function inside our action creator instead of the plain old javascript object. There is a paradigm in Redux where we dispatch two actions. First we dispatch an action saying we are LOADING, and then we make the request, and then we dispatch a second action saying we are adding the data. With Redux Thunk it is possible to dispatch multiple actions from within the returned function. 

All together, with redux thunk configured we would refactor the above example into the following. Now we only dispatch the action held within in the .then() function until AFTER the response has been received. Anything held within our .then() will not be processed until after the promise is fulfilled (we receive our data).  Our JavaScript fetch request is asynchronous, meaning the code executes on multiple threads and can multitask,  however we add a bit of structure with a .then() statement so that we don’t dispatch our action until the promise resolves. The code following the .then function will be executed asynchronously. 


In the following example, how would you expect the letters to be printed in the console? (A-E)? 

In fact, they will be printed as ACBDE. 



