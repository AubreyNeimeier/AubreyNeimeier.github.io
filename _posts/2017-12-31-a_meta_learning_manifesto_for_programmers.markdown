---
layout: post
title:      "A Meta Learning Manifesto, for Programmers. "
date:       2017-12-31 18:04:56 -0500
permalink:  a_meta_learning_manifesto_for_programmers
---


I’m completing a an intensive, 525+ curriculum hour, coding boot camp, but I’m not learning how to code. Rather, I’m learning how to learn how to code. Does that make sense? Upon completion of the program, I will have a couple languages and some web apps under my belt, but largely, I will still be a toddler in the developer world. This is because web development is expansive and constantly evolving. Languages, frameworks and libraries fall in and out of favor constantly. I could never learn every library or every programming language in a coding boot camp. So why am I shelling out the dough and time for this coding bootcamp? Because the program provides a solid foundation of computer science and problem solving, and more importantly, I will have learned how to learn how to code. I will know how to navigate web development resources, de-bug, test code, and how to methodically tackle a web app, or learn a new language entirely. These are the skills that will be my lifeline as a junior web developer. 

While I’ve been working my way through the curriculum, I’ve kept notes on the learning techniques that have helped me the most. My Meta Learning Manifesto, if you will. They are ordered to loosely reflect their significance in helping a student learn, how to learn, to code. Enjoy!

## A Meta Learning Manifesto, for Programmers
### 1.	Write pseudo code. 
Let me say it louder, for the people in the back. WRITE PSUEDO CODE. Pseudo code is an explanation of a program, or an algorithm, in layman’s terms. This is not code that a machine will read, but rather it is intended to provide an outline of the specific instructions that will later, be written in machine code. Let me show you how helpful pseudo code is for writing appropriate logic, the first time around, with an example from Avi Flobaum’s, “Hash Iteration Lab”. 

Problem Statement: “Build a method key_for_min_value that accepts an argument of a hash. This method should iterate over the hash and return the key (not the value!) that points to the smallest value of the set. If the method is called and passed an argument of an empty hash, it should return nil.”

Pseudo Code Solution: 

Define the method with one argument (a hash)

Declare variable for lowest_value, and initialize to nil

Declare variable for lowest_key (what we want to return) and initialize to nil

If hash given is empty

	Return nil
	
Iterate over the hash with an enumerable

If the value of the key/value pair is lower value than (lowest_value)

	Assign key to lowest_key 
	
	And assign the value to lowest_value (we put the next lowest value in here, it will keep re-assigning to a lower value if there is one! ) 
	
End if statement

End enumerable

Return the lowest_key

End method


My Machine Code Solution:
```
def key_for_min_value(name_hash)
  lowest_value = 1000000
  lowest_key = nil
    if name_hash.empty?
      return nil
    end
    name_hash.each do |key, value|
      if value < lowest_value
        lowest_value = value
        lowest_key = key
      end
    end
  lowest_key
end

```

Please note that while my solution passed all the tests, it is faulty because I initialized the lowest_value to a specific value. The code will break if a key/value has a greater value than 1000000. Avi's solution sets default lowest value to nil and incorporates that into if condition. 

Avi’s Solution:
```
def key_for_min_value(name_hash)
  lowest_value = nil
  lowest_key = nil
  name_hash.each do |key, value|
    if lowest_value == nil || value < lowest_value
      lowest_value = value
      lowest_key = key
    end
  end
  lowest_key
end

```
### 2.	Before coding, spend some time considering the following guiding questions. 


a.	*What is the purpose of the algorithm or program that you are writing?* 

Think about it for a second before you dive in. *What do you need the code to do?* Its purpose should be singular, simple and abstract.  Be specific about the data type of the input and outputs. For example, when writing a program that plays a game of  Tic Tac Toe we might have a method that exists solely for the purpose of converting the user input (an integer) into an index position of an array (another integer).  Taking a moment to define the specific goal of the algorithm will help with various aspects of coding  such as meaningful variable and algorithm names, guidelines for data type needed throughout, a clear idea of how the code fits within the larger program or application, etc.

b.	*What is the default return of the method you have called within your code? Is that default return appropriate? What do we need the code to return?*

c.	*What scope should the variables have? Should a variable be assigned a default value before the algorithm is called?*

### 3.	Always leave comments on your code, especially if you had a breakthrough. 

Take notes on aspects of the code you struggled with, and why. What do you consider to be the more important aspect of the code? 
If you did not write pseudo code, then consider explaining the code in layman’s terms.  This is excellent practice for the communication skills employers look for in a candidate. Speaking about your code in a way that anyone can understand is crucial to communicating effectively within your own tech team, across departments and with the public. 

### 4.	After your code passes all tests, try coding it a different way. 

Take a new approach that calls on different features of the programming language. Even if the alternative isn’t better than the original code, you will be able to make an accurate assessment of what works and doesn’t work well between your different approaches and gives you a deeper understanding of the various approaches. 

### 5.	Take notes, or at least careful mental notes, on the error messages you received, and their significance in the context of your code. 

Was the error message helpful? Did it point to an unexpected element of your code? Try to understand HOW the error message helped you(or didn’t help you) resolve the issue, and what it said the issue was. This type of information will be extremely helpful when debugging or working in a test-driven environment. 

### 6.	Don’t just ‘google it’. 

‘It’ being the question you have, or error message you are receiving. Rather, google to find an appropriate resource for the program language you are using, and THEN sift through that resource to find your solution. For example, it might seem like a good idea to google, “return array of items that match criteria, Ruby”, but really what you should google is “Ruby resources and guides”. From there you would see you need to sift through the available methods built into ruby, and find one that returns an array of all the elements which match the conditions set.  Don’t try to guess the name of the built it method either! It’s unlikely that you’ll guess the exact method name and this will only lead to useless information on methods. 


Thanks for reading! Please feel free to email me at neimeier.1@osu.edu with any comments. 




