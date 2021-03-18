# hash-tables
a hash table is a type of data structure in which the address or the index value of the element is generated from a hash-function. thus, the access of data becomes much faster.

this documentation will not go through the inner behaviour of hash-tables, as our main goal is to understand how and when to use them rather than how they are implemented. either way, i do recommend for you to go after this knowledge. it is very insightful and it will make you understand how hash tables are able to achieve this time complexities.

hash-table is a unordered collection of key-value pairs, where each key is unique. they offer a very efficient lookup insert and delete operations, that cannot be achieved by linked lists nor arrays.

### when to use it

hash tables are specially usefull when you have to do quick-search on things. see (and try to solve it), for instance [this exercise](questions/arrays/two-sum.md). as we can see, it is more efficient to do a preparation loop to build the hash table just so that we can use the quick lookup capabilities that hash tables offer. that is because hash tables are able to offer a access time of O(1).

typical questions that rely on hash tables contain requirements like this:
* search for elements on a large dataset
* store and retrieve elements from a large data set
* find duplicate elements in a data set
* whenever you have a nested loop, consider hash tables

it does not make sense to use this kind of data structure when you are expecting some kind of sorting in your data.

### questions to exercise it
[two sum](questions/arrays/two-sum.md)


## _examples_

### accessing items 

```python
descriptive_numbers = {
		1: "one",
		2: "two"
}
x = descriptive_numbers[1]
```
_complexity_: O (1)


### updating items 

```python
example_dict["example_key"] = "example description"
```
_complexity_: O (1)

### deleting items 

```python
example_dict.pop("example key") #this also returns the value
```
_complexity_: O (1)

### check if key exists in hash table items 

```python
if "key" in example_dict: 
```
_complexity_: O (1)

### return all keys in dict 

```python
example_dict.keys(): 
```
_complexity_: on python 2, it's O(n) and builds a new list. in python 3, it's O(1).
