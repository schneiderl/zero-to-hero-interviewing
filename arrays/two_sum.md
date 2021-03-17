
# two sum

[question link](https://leetcode.com/problems/two-sum/)

**problem statement:**
given an array of integers  `nums` and an integer  `target`, return  _indices of the two numbers such that they add up to  `target`_.
you may assume that each input would have  **_exactly_  one solution**, and you may not use the  _same_  element twice.
you can return the answer in any order.

**example:**

**input:** nums = [2,7,11,15], target = 9

**output:** [0,1]

**output explanation** because nums[0] + nums[1] == 9, we return [0, 1].


## first approach: brute force
the most naive and simple approach to this problem would be to just loop through all elements in `nums` and sum it up with all subsequent elements. if the result of that sum adds up to the `target`, the result indexes have ben found
```python
    def twoSum(self, nums, target):
        for x in range(0, len(nums)):
            for y in range(x+1, len(nums)):
                if nums[x]+nums[y] == target:
                    return [x, y]
```
**time complexity:** O(n^2)

time complexity due to a double index lookup (double loop)

**space complexity**: O(1)

## second approach: use a hash table

the time complexity from the first approach can be improved.
the complexity of the first approach is built upon the double lookup on the input array.
we may reduce index lookup complexity by using a hash table.
```python
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_dict = {}
        for x in range(len(nums)):
            nums_dict[nums[x]] = x #build hash table in format {num:idx}
            for x in range(len(nums)):
                search_target = target - nums[x]
                # this second part of the if is necessary to avoid a number adding to itself
                if search_target in nums_dict and nums_dict[search_target] != x:
                    return [x, nums_dict[search_target]]
```
**time complexity:** O(n)

time complexity reduced from exponential to linear by using hash-table lookup capabilities.

**space complexity**: O(1)

#
topics: arrays, hash-table
