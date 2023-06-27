### 75. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Sort Colors

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/sort-colors/)*</i>

Given an array `nums` with `n` objects colored red, white, or blue, sort them **[in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** so that objects of the same color are adjacent, with the colors in the order red, white, and blue. We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively. You must solve this problem without using the library's sort function.

给定一个包含红色、白色和蓝色、共 n 个元素的数组 nums ，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。 我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。 必须在不使用库内置的 sort 函数的情况下解决这个问题。

```python
# Example 1
nums = [2,0,2,1,1,0] # Input
[0,0,1,1,2,2] # Output


# Example 2
nums = [2,0,1] # Input
[-1,0,3,4,5] # Output

```

#### Solution

A trick is to count the number of different colors. Since there are only three colors, we will simply loop all three of them.  Next, we can replace each number in `num` with those in the `output` list.

我们可以数一下每个颜色有几个, 然后替换`nums` 的数值。

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        output = []
        for color in [0, 1, 2]:
            if color in nums:
                output += [color] * nums.count(color)
        for i in range(len(nums)):
            nums[i] = output[i]
```
