
# arrays
arrays are data structures consisting of a collection of elements, each identified by a index or key. the access to data can be done directly via the index or traversing through the array and checking for the needed values.

you will very commonly find arrays as a part of your interview questions, specially as input/expected output parameters

* please notice that traversing through an array can be costful, specially if your doing it more than once. you might want to consider the use of hash-tables in some cases.

## _examples_
### traversing 
```python
for item in array:
    print(item)
```
_complexity_: O (n)

### appending 
```python
array.append(7)
```
_complexity_: O (1)
### deletion
```python
array.pop(index)
```
_complexity_: O (n)

### search by index
```python
array.index(1)
```
_complexity_: O (1)

### search by value
search by value is done by traversing through array and checking each value
_complexity_: O (1)

### update
```python
array[index] = updated_value
```
_complexity_: O (1)
