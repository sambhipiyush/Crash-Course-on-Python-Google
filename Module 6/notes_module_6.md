Crash Course on Python
=======================

by Google

# Module 6
#
## Title: Final Project

### Writing a Script from the Groung Up

#### Problem Statement

* Each **event** is an instance of the **event class**
* An **event class** contains the date when the event happened, the name of the machine where it happened, the user involved, and the event type

#### Research

* The difference between sort method and sorted function : **sort method** modifies the list it's executed on, while the **sorted function** returns a new list that's been sorted
* **sorted** returns a new list, while **sort** returns the same list reorganized
	```python
	>>> numbers = [4, 6, 2, 7, 1]
	>>> numbers.sort()
	>>> print(numbers)
		[1, 2, 4, 6, 7]
	>>> names = ['Carlos', 'Ray', 'Alex', 'Kelly']
	>>> print(names)
		['Carlos', 'Ray', 'Alex', 'Kelly']
	>>> print(sorted(names))
		['Alex', 'Carlos', 'Kelly', 'Ray']
	>>> print(names)
		['Carlos', 'Ray', 'Alex', 'Kelly']
	>>>
	>>> # To organize/sort list by different criteria
	>>> # We will use "key" param for this
	>>> print(sorted(names, key=len))
		['Ray', 'Alex', 'Kelly', 'Carlos']
	```

#### Writing a Script

> Separating functions is helpful when debugging or making other changes, as it keeps functions from getting ‘tangled’. It also makes it easier to adapt functions for other uses

```python
>>> def get_event_date(event):
>>> 	return event.date
>>> 
>>> def current_users(events):
>>> 	events.sort(key=get_event_date)
>>> 	machines = {}
>>> 	for event in events:
>>> 		if event.machien not in machines:
>>> 			machines[event.machine] = set()
>>> 		if event.type == 'login':
>>> 			machines[event.machine].add(event.user)
>>> 		elif event.type == 'logout':
>>> 			machines[event.machine].remove(event.user)
>>> 	return machines
>>> 
>>> def generate_report(machines):
>>> 	for machine, users in machines.items():
>>> 		if len(users) > 0:
>>> 			user_list = ", ".join(users)
>>> 			print('{}: {}'.format(machine, user_list))
```

### Final Project

#### Final Project

* A word cloud is an image that's made up of different sized words. Usually the sizes of the words are determined by how many times each word appears in a specific text
* To create the image itself, we're going to use an external Python module called creatively Word cloud
