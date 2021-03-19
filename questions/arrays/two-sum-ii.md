
# two sum ii

[question link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

**problem statement:**
given an array of integers  `nums` that is sorted in ascending order  and an integer  `target`, return  _indexes (1-indexed) of the two numbers such that they add up to  `target`_.
you may assume that each input would have  **_exactly_  one solution**, and you may not use the  _same_  element twice.
you can return the answer in any order.

**example:**

**input:** nums = [2,7,11,15], target = 9

**output:** [1,2]

**output explanation** the sum of 2 and 9 is 7, therefore, the 1-indexed indexes are 1 and 2


## first approach: brute force
the most naive and simple approach to this problem would be to just loop through all elements in `nums` and sum it up with all subsequent elements. if the result of that sum adds up to the `target`, the result indexes have ben found
```python
def twoSum(self, nums, target):
    for x in range(0, len(nums)):
        for y in range(x+1, len(nums)):
            if nums[x]+nums[y] == target:
                return [x+1, y+1]
```
**time complexity:** O(n^2)

time complexity due to a double index lookup (nested loop)

**space complexity**: O(1)

with this approach we are completly ignoring the fact that the array is sorted. as we have seen on [two-pointers](../../two-pointers.md), when we have a search for multiple items in a sorted array, we might want to consider a two pointers approach.


## second approach: two pointers

we can take use of the charateristic of the array of already being sorted to avoid a nested loop. using the two pointer technique we can set a pointer at the left of the array and one at the right and start summing up the items and comparing it to the target. if the value is lower than target, we move the left pointer to the right. if it is higher, we move the right pointer to the left. 

```python
def twoSum(self, nums, target):
    left_pointer = 0
    right_pointer = len(nums) - 1
    while left_pointer < right_pointer:
        if nums[left_pointer] + nums[right_pointer] == target:
            return [left_pointer+1, right_pointer+1] # +1 needed due to 1-indexed behavior
        if nums[left_pointer] + nums[right_pointer] > target:
            right_pointer -= 1
        if nums[left_pointer] + nums[r] < target:
            left_pointer +=  1

```
**time complexity:** O(n)

complexity is O(n) because we would have to traverse through the list of nums. 

**space complexity**: O(1)


#
topics: [arrays](../../arrays.md), [two-pointers](../../two-pointers.md)
