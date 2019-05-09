---
layout: post
title:      "Synchronous and Asychronous JavaScript, and Fetch Requests"
date:       2019-05-09 16:53:45 -0400
permalink:  synchronous_and_asychronous_javascript_and_fetch_requests
---


Let’s start with the basics. Generally speaking, JavaScript is single threaded, meaning everything else in the subsequent code is blocked until the current task is completed. Essentially, each operation occurs in order, one after another.  We call this work flow synchronous. Most operations in javascript are performed synchronously. However, there are some disadvantages to synchronous code. Because each action is ‘blocking’, the DOM is paused/frozen or unavailable until the task is complete, leaving the user waiting on a locked browser to open up. If we need to load a bunch of data, the browser may lock up for an unreasonable amount of time while the data is loading. This is unpleasant for the user! 

We want the user to continue to interact and view the page while the data is loading in the background. In order to make this happen, we can use asynchronous code! Asynchronous is the opposite of synchronous - your code continues to run while a time consuming task in being run in the background! Before we move on, let's summarize what we’ve learned so far. 

Synchronous - code is executed in sequence, blocking each subsequent statement from executing until the current one is finished. 

Asynchronous - code executes on multiple threads, meaning many tasks can be completed at once. The order of invocation is sequential, but each task is non blocking so as soon as one tasks begins, the next can start, reducing wait time for the user. 

Web requests in JavaScript are Asynchronous! When we request data from an API, the code following will start running BEFORE the web requests resolves. When the web request resolves we say the promise has resolved. Read more about promises[ here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). This can pose a problem because often we want to manipulate or send the received data in the following code, and if the code is processed before we receive the data, we will run into serious problems! For example, 

```
function getDogs(){
    const dogs = fetch('https://wwww.dogsAPI.com')
    return {
        type: FETCH_DOGS,
        dogs
    }
}


```



The action creator of type ‘FETCH_DOGS’ would be dispatched before the response is received. To resolve this problem we can chain a .then() function onto the request, so that our action is not dispatched until we receive our data. Additionally another standard practice is to incorporate Redux Thunk middleware, which allows us to return a function inside our action creator instead of the plain old javascript object. There is a paradigm in Redux where we dispatch two actions. First we dispatch an action saying we are LOADING, and then we make the request, and then we dispatch a second action saying we are adding the data. With Redux Thunk it is possible to dispatch multiple actions from within the returned function. 

All together, with redux thunk configured we would refactor the above example into the following.

```
export function getDogs() {
    return (dispatch) => {
      dispatch({ type: 'START_ADDING_DOGS_REQUEST' });
      return fetch('http://www.dogsAPI.com')
        .then(response => response.json())
        .then(cats => dispatch({ type: 'FETCH_DOGS', dogs }));
    };
  }

```

Now we only dispatch the action held within in the .then() function until AFTER the response has been received. Anything held within our .then() will not be processed until after the promise is fulfilled (we receive our data).  Our JavaScript fetch request is asynchronous, meaning the code executes on multiple threads and can multitask,  however we add a bit of structure with a .then() statement so that we don’t dispatch our action until the promise resolves. The code following the .then function will be executed asynchronously. 


In the following example, how would you expect the letters to be printed in the console? (A-E)? 

In fact, they will be printed as ACBD( E never prints).

```
handleSubmitEntry = (e) => {
        e.preventDefault()
        console.log('A') //////////////////////////////////////////////////////////
        this.props.createEntry(this.state)
        console.log('B') //////////////////////////////////////////////////////////
        this.setState({
            entryContent: " "
        })
    }
		
export const createEntry = entry => {
    console.log('C') ////////////////////////////////////////////////////////////////////
    let data = {
      method: 'POST',
      headers: {
        'Accept': 'application/json',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
            cuid: cuid(),
            date: new Date().toUTCString(),
            entry_text: entry.entryContent
       })
    }  
        return dispatch => {
            fetch(`http://localhost:3001/entries`, data)
            .then(response => response.json())
            .then(new_entry => {
              console.log('D') //////////////////////////////////////////////////////
              dispatch({
                type: 'CREATE_ENTRY',
                payload: new_entry
            })})
            .catch(err => err)
        }
        console.log('E')/////////////////////////////////////////////////////
    }


```


The first letter is easy. We trigger handleSubmitEntry when we click the submit button. The letter A prints to the screen. Then we invoke createEntry and will see C printed. Then we would expect to see D printed next right? However the fetch request is asychrnous and is taking some time.... Nothing in the .then() functions will we executed until AFTER the fetch request completely resolves. Since this is taking some time, the processor moves on and goes BACK into handleSubmitEntry, where we print the letter B. We reset the form to have a blank feild and by this time, the fetch request has resolved, so we pick up where we left off there at .then(response => response.json())...  within the fetch request. The E is never printed because it is written after a return statement! 


Helpful Resources on this topic
1. [Asynchronous JavaScript Intro](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing)
2.  [Asynch](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts)
 

 



