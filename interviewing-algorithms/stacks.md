# stacks

a stack is a linear data structure on which elements are stacked on top of each other and only the last element added to the structure can be accessed. that being said a stack is a **last in first out**.

this data structure is particularly useful when the order of action is important. when you have to make sure certain things are executed before others, you might want to consider using a stack. 

the most classical example of the use of a stack is the `ctrl+z` functionality when your editing a text document, for instance. every change on the text is piled up on the stack, so when you hit `ctrl+z` the last change you've made on the document is removed from the top of the stack and the changes are reverted.

another good example is the call stack of a program. when a new function is called, the function gets added to the stack. when the newly called function returns a response, the function is no longer being executed, thus it can be removed from the stack.

lets get into a more practical example.

let's say we want to implement a text editor that allows backspaces, we receive as input what was typed on the keyboard:

`input ="abcd#e#f#", 
 "#" meaning the backspaces`

what would be the end status of our text editor? 

the final output would be `abc` as all the other letters were backspaced.

we can solve this using a stack like in the code below:

```python
def text_editor(input):
	text_stack = []
	for char in input:
		if char == "#": #removing the last letter typed
			text_stack.pop()
		else:
			text_stack.append(char)
	return str(text_stack)
```

_please beware that the examples do not handle some edge cases, it simply tries to explain the concept._



### when to use it

typical questions that rely on hash tables contain requirements like this:
* the code has to respect some order of precedence. for instance, parenthesis on arithmetic operations
* reverse the input elements
* store the result of previous operations to compute future operations
* compute the current status of the application or data based on previous status changes

### questions to exercise it
[crawler log folder](questions/stacks/crawler-log-folder.md)


## _examples_

in python, stacks can be implemented using lists and its operations.

the list function `.pop()` removes the last element with O(1) time complexity, while the function `.append()` adds a new element at the end of the list with O(1) complexity. those are all the necessary operations for a last in first out queue. 


### creating a stack and appending items to it

```python
stack = []
stack.append("first item")
stack.append("second item")
```

_complexity_: O (1)


### retriving items from stack

```python
stack = []
stack.append("first item")
stack.append("second item")
print(stack.pop()) #prints: "second item"
				   #this removes the last item from the stack
```

_complexity_: O (1)




### read last element without removing it 

```python
stack = []
stack.append("first item")
stack.append("second item")
print(stack[-1]) # prints: "second item"
				 # does not remove the item
```

_complexity_: O (1)




