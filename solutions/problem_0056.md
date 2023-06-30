### 56. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Merge Intervals - 合并区间

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/merge-intervals/)*</i>

Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return *an array of the non-overlapping intervals that cover all the intervals in the input*.

给定一个会议时间安排的数组 intervals ，每个会议时间都会包括开始和结束的时间 intervals[i] = [starti, endi] ，请你判断一个人是否能够参加这里面的全部会议。

```python
# Example 1
intervals = [[1,3],[2,6],[8,10],[15,18]] # Input
# Output [[1,6],[8,10],[15,18]]


# Example 2
intervals = [[1,4],[4,5]] # Input
# Output [[1,5]]
```

#### Solution

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if len(intervals) < 1:
            return intervals

        # simply define the start of the output as the first interval
        # 预设output的第一个interval
        output = [intervals[0]]

        """
        To start the loop, set i and j as 0
        - i: current index of the time intervals being processed
        - j: index of the last time intervals processed 
             in the temporary output list
        ---------------------------------------------------------
        我们需要一步步去比较会议时间段，和暂时整理好的output。
        我们会从0开始我们的循坏，于是，我们把i和j都设为0。
        - i：我们目前正在处理时间段的排序
        - j: 我么已经处理好的output时间段的排序
        """
        i, j = 0, 0
        while i < len(intervals):
            oCur = output[j]
            iCur = intervals[i]
            # check if the start of the iCur falls within the oCur
            # 检查一下记录里会议开始时间比前一个时间段的结束时间靠前
            if iCur[0] <= oCur[1]:
                # if yes, merge the intervals， 如果是的话，我们可以合并
                output[j] = [oCur[0], iCur[1]]
            else:
                # if now, just append the intervals to the sorted list
                # 如果不是，讲这个时间段添加到output
                output.append(iCur)
                j += 1
            i += 1
        return output
```
