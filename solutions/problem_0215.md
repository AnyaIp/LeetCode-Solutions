### 215. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Kth Largest Element in an Array - 数组中第k大的数字

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/)*</i>

Given an integer array `nums` and an integer `k`, return *the* `kth` *largest element in the array*. Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.  Can you solve it without sorting?

给定整数数组 nums 和整数 k，请返回数组中第 k 个最大的元素。

请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

你必须设计并实现时间复杂度为 O(n) 的算法解决此问题。

```python
# Example 1
nums, k = [3,2,1,5,6,4], 2 # Input
# Output 5 

# Example 2
nums, k = [3,2,3,1,2,4,5,5,6], 4 # Input
# Output 4 
```

#### Solution

We can use heapq.nlargest to select the kth largest elements, and return the smallest number among them. 我们可以运用heapq.nlargest选择第k个最大的元素。

```python
import heapq as hq

class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        if len(nums) == 1:
            return nums[0]
        heap = []
        for n in nums:
            hq.heappush(heap, n)
        max_nums = hq.nlargest(k, heap)
        return max_nums[-1]
```
