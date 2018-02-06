---
layout: post
title:      "Class Variables and Methods Lab"
date:       2018-02-06 19:27:41 +0000
permalink:  class_variables_and_methods_lab
---


### This lab has the following problem statement: Define a method that returns a hash of unique genres and the number of songs in each genre. 
For example:
```
genre_count = {"rap" => 3, "rock" => 2, "pop" => 1}

```
We start with a class variable, @@genres which is an array of genres. This array includes duplicates of genres. For example: 
``` 
@@genres = ["rap", "rock", "rock", "rap", "rap", "pop"]

```

At this point you have probably guessed that we will use an enumberable to interate over each element of the @@genres array, in order to extract and count the unique genres. 

### First let's write some psuedo code: 

```
def self.genre_count
for #each unique genre
count how many times the genre occurs in @@genres
add key value pair to hash
return the hash

```

We know that the method must be a class method, as it acts on a class variable and the method is generally related to the entire class, not just a single instance! Now that we have a good start on the code logic in psuedo code, lets turn that into machine code. 

### my solution: 
```
def self.genre_count
count = 0
new_hash = {}
@@genres.uniq each do |genre|
     count = @@genres.count {|x| x ==genre}
		 new_hash[genre] = count
		 end
	new_hash
end
 ```
 
 I count the times the uniq genre occurs by iterating over @@genres.uniq. Then I build a hash key value pair with the unique genre as the key, and the count as the value. 
 
 Avi's solution is a bit different and includes an important syntax pattern that has proved to be the eloquent solution to MANY other labs. 
###  Avi's Solution
 
 ``` 
 def self.genre_count
   genre_count = {}
	 @@genres.each do |genre|
	    if genre_count[genre] 
			   genre_count[genre] += 1
			else
			   genre_count[genre] = 1
			end
			
	end
	genre_count
	end
			
	``` 
	What does the following line mean? 
	```
	if genre[count]
	```
	
	It seems too open ended and unfinished to be an if statement condition! The syntax is a bit strange but the above line translates to: "If genre_count[genre] exists (aka if genre_count for the key [genre] exists) then complete the following. " 
	
so all together the logic reads:
``` if genre_count of key "genre" exists
         then increment it's count (the value of the key value pair) by one. 
			else (if genre_count of key "genre" is nil, or falsey, aka it doesn't exist)
			   then CREATE the value/key pair for that genre and set it to one.
				```
				
				This is a common pattern which extremely simplified looks like: 
				
				if <thing>       //if thing exists
				   do something 
				else                // if it doesn't exist
				   do something else
					 
				Thanks for reading and best of luck with your OO Ruby! 
					 
					 
				 
				 
			
			


	
	 






