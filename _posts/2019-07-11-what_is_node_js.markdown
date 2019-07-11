---
layout: post
title:      "What is Node.js"
date:       2019-07-11 16:12:04 -0400
permalink:  what_is_node_js
---

According to [LearnCodeAcademy’s video on Node JS](https://www.youtube.com/watch?v=pU9Q6oiQNd0), the following is a brief intro to Node.js. The creators of Node, took JavaScript, which is normally confined to a web browser, and they allowed it to run on your computer. A JavaScript engine for google chrome can now run on your machine. JavaScript in this new environment allows us to do things like;  listen for network traffic, access files on our computer, listen to HTTP requests your computer receives and send back a file. 

Basically anything you could do in PHP or RoR you can now do in JS, through Node.js
## Two main pillars of use
Front end development, making utilities on your machine - things that help you build and write JavaScript code. 
Back End Development/Engineering - designing web based application with frameworks like (Express and Koa - similar to RoR)
### Some key points on Node.js are listed below; 

* There is no WINDOW, or window scope since we aren’t operating in console/browser, but there IS a global object. There is also no document object. 
* We execute files by typing $ node module1.js $ in the shell, and it executes whatever is in the module1.js file. 
* Modules are pockets of code that we export and import to build larger objects. 
* NPM = node package manager  - allows you to download and manage and produce modules(packages) for export. Handles dependencies, Modular modules … DUH! 
* We can bundle our own package with $ npm init … then $ npm install backbone -S $ which saves our package/dependency info in the package.json file. 
* $ npm install will install all the dependencies. Node has access to 1000’s of packages - like ruby gems.  
* We use a package called http to run/create a web server. It’s built into node.js

