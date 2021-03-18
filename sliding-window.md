# sliding-window

please do not read this without first reading [two pointers](two-pointers.md) - they are very similar concepts and while two pointers can be understood without sliding windows, sliding windows are best understood when you already have two pointers figured out.

now lets go to the content

sliding window technique does pretty much what the name says: a window is formed over some part of the data and that window can move so that different parts of the data can be captured.

there are two main forms of using sliding windows

**1. fixed size sliding window:**

let's say a problem asks you to find the maximum sum of two adjacent values on a input array. this is a perfect candidate for using sliding windows and the question requirement fixes the size of array to 2. 

```
  input = [1,1,2,3,1]
  expected output = 5
  output explanation: the maximum sum value of two adjacent elements is 5 (2+3)
```

to solve this with sliding windows we simply set a pointer to the position zero and the other one positions to the right and start shifting both pointers to the right, calculating and storing the maximum sum. 

code can be found below:

```python
def maximum(input_array):
	left_pointer = 0
	right_pointer = 1
	max_sum = 0
	while right_pointer < len(input_array):
		max_sum = max(max_sum, input_array[left_pointer]+input_array[right_pointer])
	return max_sum
```
_please beware that the examples do not handle some edge cases, it simply tries to explain the concept._

**2. flexible size sliding window:**

lets use as example the following problem: you are asked to return the maximum lenght of a contiguous subarray for which the sum of the items is less than 5.

```
  input = [1,1,2,3,1]
  expected output = 3
  output explanation: the maximum length for which the sum of items is less than 5 is 4 (1+1+2)
```

you are unsure of what is length of the subarray, thus, the sliding window is flexible. 

to solve this we can create a window with both pointers on the first item. if adding the next item to the window does not overflow the sum of 5, you just simply move one of the pointers (the right most) to the right. if it does overflow, just move your other pointer to the right. 

always keep track of what is the maximum lenght that you subarrays (`right_pointer - left_pointer`) had

```python
def maximum_lenght(input_array):
	left_pointer = 0
	right_pointer = 0
	max_length = 0
	while right_pointer < len(input_array):
		if sum(input_array[left_pointer:right_pointer] < 5):
			right_pointer +=1
		else:
			left_pointer +=1
		max_length = max(max_length, max(right_pointer-left_pointer))
	return max_length
```
_please beware that the examples do not handle some edge cases, it simply tries to explain the concept._


### when to use it
a question that uses a list or string that must be iterated in sequence is usually a good candidate for sliding window. you will usually want to consider to use sliding window when you requirement gives you some hint that you will have to consider adjacent elements. 

typical questions that rely on sliding windows contain requirements like this:
* longest value
* longest/shortest subsequence
* mininum/maximum sum of contiguous elements 


### questions to exercise it
