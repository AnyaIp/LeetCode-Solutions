### 27. <span style="color:#08979c;background:#e6fffb;border-color:#87e8de;padding:1px 6px;border-radius:5px;">Easy</span> Remove Element - 移除元素

<i style="float:right">Source: [LeetCode](https://leetcode.com/problems/remove-element/)</i>

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm). The order of the elements may be changed. Then return *the number of elements in* `nums` *which are not equal to* `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。 不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

```python
# Example 1
nums, val = [3,2,2,3], 3 # Input
# Output 2, [2,2,_,_]


# Example 2
nums, val = [0,1,2,2,3,0,4,2], 2 # Input
# Output 5, [0,1,4,0,3,_,_,_]
```

#### Solution

It is required that the numbers must be modified in place without generating any new list. In this case, we can simply ignore target numbers (those equal to `val`) and keep the rest in front. We use `j` to record the length of numbers that are not equal to `val`.

值得注意的是，我们不可以使用额外的数组，同时我们只需要让符合规定（不等于`k`的数值）永远在最前面。这么一来，一个简单的做法是，直接忽略那些等于`k`的数值。我们用`j`来记录符合数组的长度。

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i, j = 0, 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[j] = nums[i]
                j += 1
        return j
```
