---
layout: post
title:      "SoundTrack "
date:       2019-04-17 00:34:58 +0000
permalink:  soundtrack
---

Do you ever feel intese nostalgia when hearing a song? When the music that's playing brings your right back to a certain memory, city, or time in your life? SoundTrack is a journal platform, that will eventually leverage Spotify's API so that music and memories can interwine like they do in real life. 

This project meets all the requirements and then some, but needs to be build out some. For now, users can login/signup and record their thoughts. All the previous journal entries are sorted by descending date, so that the most recent journal entry is listed at the top. It sounds so simple but let me explain a bit more. User data, such as login info and the journal entry data is recorded in a rails API that I built and configured to the React-Redux front end system that the user is interacting with. It is a bit of a challenge to configure this type of environment for development, and it also complicates the work flow of an action in the browser. For example, when the user clicks Login, this is the following chain of events


1.  The click triggers an action function, passing in the username and password entered
2.  The action function makes a POST request to my rails api at the url http://localhost:3001/sessions, with the user info mentioned. 
3.  The Rails API processes this request in the Create action of the sessions controller. If the login info is correct, then JSON info about the user is sent back to the original action function.
4.  Another action is dispatched, so that the user info can be saved in the component state. THis is done with the reducer built on the front end. 
5.  Finally, if the user was succesfully logged in, React Router changes the URL in the browser to '/entries' and the entries are listed. 

OR simplified

1. User clicks button
2. We verify data is good(by checking our backend DB)
3. We might also send data to component state (dispatched to the reducer)
4. Users browsers change and we see the next page (entries) 


Essentially, all data is saved on the API backend, so various actions in the front end will trigger FETCH requests to pull or manipulate that data. The data recieved is sometimes also sent to component state, making it available more immediately in the front end.





