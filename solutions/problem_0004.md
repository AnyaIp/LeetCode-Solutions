### 4. <span style="color:#cf1322;background:#fff1f0;border-color:#ffa39e;padding:1px 6px;border-radius:5px;">Hard</span> Median of Two Sorted Arrays

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/)*</i>

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays. The overall run time complexity should be `O(log (m+n))`.

给定两个大小分别为 m 和 n 的正序（从小到大）数组 nums1 和 nums2。请你找出并返回这两个正序数组的 中位数 。算法的时间复杂度应该为 O(log (m+n)) 。

```python
# Example 1
nums1, nums2 = [1,3], [2] # Input
2.00000 # Output

# Example 2
nums1, nums2 = [1,2], [3,4] # Input
2.50000 # Output
```

#### Solution

We can apply **floor division** `//` here. If the length of the number list is an odd number, the median is the number in the middle. Else if the length of the number list is  an even number, we take the mean of the two numbers in the middle.

我们可以利用`//` 向下除法。



```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        nums = nums1 + nums2
        nums.sort()
        if len(nums) % 2 != 0:
            i = len(nums) // 2
            med = nums[i]
        else:
            i2 = len(nums) // 2
            i1 = i2 - 1
            med = (nums[i1] + nums[i2]) / 2
        return med
```
