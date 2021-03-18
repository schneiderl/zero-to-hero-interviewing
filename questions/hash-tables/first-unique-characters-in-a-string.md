# first unique characters in a string

[question link](https://leetcode.com/problems/first-unique-character-in-a-string/)

**problem statement:**
given a string, find the first non-repeating character in it and return its index. if it doesn't exist, return -1

**example:**

**input:** "leetcode"

**output:** 0

**input:** "loveleetcode"

**output:** 2


## first approach

the most naive approach would be to doubly iterate through the array, checking if there is a repeating character on the array. if there is not, then return the current index

```python
for x in range (0, len(s)-1):
	found_equal = False
	for i in range (x+1, len(s)):
		if s[x] == s[i]:
			found_equal = True
	if found_equal == False:
		return x
return -1
```
_complexity: O(n^2)_ due to the nested loop

as we have seen on [hash-tables](hash-tables.md), whenever there is a nested loop, we might want to consider a hash-table solution. thus, the approach below.

## second approach

a good approach to this would be to use a hash table key-value pairs functionality to keep track of the count of each element on the string. afterwards, with the counted elements in hand, we just loop through the counted results and return whenever we find a 1.

**wouldn't that be two loops?** yes, it would. one to count the values and one to find a key where the value is 1. that would result on a time complexity of O(n*2), which simplifies to O(n) 

```python
char_count = {}
for char in s:
	if item in char_count:
		char_count[item] += 1
	else:
		char_count[item] = 1

for key, value in char_count.items():
	if value == 1:
		return (s.index(key))
return -1

```
_complexity:_ O(n*2) -> O(n) 


#
topics: [hash-table](hash-table.md)