---
layout: post
title:      "Key take-aways from the Collaborating Objects Lab"
date:       2018-01-23 08:10:37 -0500
permalink:  key_take-aways_from_the_collaborating_objects_lab
---



The collaborating objects lab presents a new challenge to us as we have to define methods and variables which have specific relationships to each other. For example, a method definition might call on a series of other methods depending on if it meets the criteria set. The subsequent methods will have to then assign attributes correctly and consistently throughout so that all the instances of the classes are account for appropriately. 

Additionally, we are creating instances in a variety of methods, rather than simply the initialize and new method. After struggling through this lab for a couple days, I’ve rounded up by most essential notes that helped me through this lab. 

## Before defining any method, you must first determine if that method should be an instance method or a class method.
To help you determine this, here is a quick reference guide: 

### Instance methods 
•	Methods that belong only to that class and that class’s instances. For example

### Class methods

•	A method that is called on the class itself. 
•	We use class variables to keep track of all the instances of a class
•	Self within a class method is the class itself	
•	With an example of a constructor 

### Every collectible item should be self-aware of its owner

Every time we add instances to a collection, we should tell the instance who’s collection they’ve been added to. 

`@Aubrey’s_plants = [“fern”, “cactus”, “succulent”] `

But for all fern knows, he’s one of Bob’s plants, or Jane’s plants. Fern doesn’t know who it’s owner is yet because we never told it!! So a good rule of thumb: Every time you shovel an instance into a collection, whether it’s an instance variable or a class variable, consider this. Does the instance need to know it’s owner? Or more generally, does the does the instance need to be self-aware when it comes to the attributes related to the collection?  Well if we want to be able to say:

`fern.owner #=> Aubrey `

Then yes! Tell the instance who it belongs to as soon as you shovel it into the collection. 

Here's an example of how you can make the instance self-aware

```
Def add_plant(plant)
	@Aubreys_plants << plant
	Plant.owner = self 
End
```

### 



