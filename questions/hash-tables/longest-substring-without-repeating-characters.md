# longest substring without repeating characters

[question link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

**problem statement:**
given a string s, find the length of the longest substring without repeating characters.

**example:**

**input:** "abcabcbb"

**output:** 3

**explanation:** the answer is "abc", with the length of 3

**input:** "bbbbb"

**output:** 1

**explanation:** the answer is "b", with the length of 1

## first approach

the most naive approach would be to build all substrings and then iterate through them checking if they are formed by unique characters.

the time complexity here would be enormous (O(n^3)) - see the code below for reference

nested loop while constructing the substrings * O(n) for checking it's uniqueness

```python
def is_unique(substring):
	sets = set()
	for char in substring:
		if char in charset:
			return False
		else:
			charset.add(char)
	return true


def lengthOfLongestSubstring(self, s: str) -> int:
         max_length = 0
         # Itrate over the all possible substring and check it is unique
         for i in range(len(s)):
             for j in range(i, len(s)):
                 if check_unique(s[i:j+1]):
                     max_length = max(max_length, j - i + 1)
         return max_length
```

as we have seen on [two-pointers](../../two-pointers.md), usually when there is a nested loop in the solution, there is a better way to solve it.
that being said, take a look at the secon approach.


## second approach

the first approach solves the problem, but it is too slow and wouldn't be accepted as a solution.

in the problem description we are asked to find the **longest** substring. read substring as a **contiguous** set of chars inside a string. 

the keywords **longest** and **contiguous** raise a big flag for the use of [sliding-windows](../../sliding-window.md).

the second approach aims on forming a sliding window with flexible size over our data. we increase the size (right pointer to the right) of the sliding window while the next char is not found on the window. if the char is found, we decrease the size of the window (left pointer to the right) until the next char can't be found on the sliding window. if we keep track of the maximum window size at each iteration, we have the response. 

we could specifically check if the next element is already inside the formed window, but that would take O(n), if we multiply that for the time complexity it takes to loop through all the array, we have O(N^2), which is better than the previous, but not quite otpimal. thus, we choose to use a **hashset**.

code can be found below

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        chars = [0] * 128

        left, right = 0, 0

        maximum_window_size = 0
        while right < len(s):
            r = s[right]
            chars[ord(r)] += 1 #ord() function returns the number representing the unicode code of a specified character

            while chars[ord(r)] > 1: # if the next char is already found on the hashset, we slide the left side of the window to the left
                l = s[left]
                chars[ord(l)] -= 1
                left += 1

            res = max(res, right - left + 1)
            right += 1	# we are sure that adding the next char to the window will not cause it to have duplicates on the window. slide window to the right
        return res
```
_please beware that the examples do not handle some edge cases, it simply tries to explain the concept._


by using both [sliding-windows](../../sliding-window.md) and a **hashset**, we are able to reduce the time complexity from the initial O(n^3) to O(n)
#
topics: [hash-table](../../hash-table.md), [two-pointers](../../two-pointers.md), [sliding-window](../../sliding-window.md)
