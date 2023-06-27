### 179. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Largest Number

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/largest-number/)*</i>

Given a list of non-negative integers `nums`, arrange them such that they form the largest number and return it. Since the result may be very large, so you need to return a string instead of an integer.

给定一组非负整数 `nums`，重新排列每个数的顺序（每个数不可拆分）使之组成一个最大的整数。**注意**: 输出结果可能非常大，所以你需要返回一个字符串而不是整数

```python
# Example 1
nums = [10,2] # Input
"210 # Output


# Example 2
nums = [3,30,34,5,9] # Input
"9534330" # Output
```

#### Solution

We use `__lt__` operator to compare combinations of two numbers. If all numbers are 0, simply return `'0'` as output.

```python
class compare(str):
    def __lt__(x, y):
        return x + y > y + x
        
class Solution:
    def largestNumber(self, nums):
        if all([x == 0 for x in nums]):
            return '0'
        largest_num = sorted(map(str, nums), key=compare)
        largest_num = ''.join(largest_num)
        return largest_num
```
