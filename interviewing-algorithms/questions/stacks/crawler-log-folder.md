# crawler log folder

[question link](https://leetcode.com/problems/crawler-log-folder/)

**problem statement:**
a filesystem keeps a log each time a user performs a change folder operation. the possible operations are described belo:

- `"../"` : move to the parent folder
- `"./"` : remain on the same folder
- `"x/"` : move to the child folder named x

the input is a array of operations performed by the user. after all the operations are concluded, return the number of operations needed to go back to the main folder 


**example:**

**input:** `logs = ["d1/","d2/","../","d21/","./"]`

**output:** 2

**output explanation** use this change folder operation "../" 2 times and go back to the main folder.


## first approach

as stated on [stacks](../../stacks.md), they are best used when you have to `"store the result of previous operations to compute future operations"`, which is exactly the case here. 

in order to compute how many operations we would need to execute to go back to the root, we have to first understand where are we based on the input operations.

a simple approach to this problem would be to use a stack and execute the whole list of input operations, as follows:

```python
def minOperations(self, logs: List[str]) -> int:
    tree = []
    for log in logs:
        if log == "../":
            if len(tree) != 0:
                tree.pop()
        elif log == "./":
            pass
        else:
            tree.append(log)
    return len(tree)
```

_complexity_: O(n) since we are looping at the input and doing constant time operations on the stack


#
topics: [arrays](../../stacks.md)
