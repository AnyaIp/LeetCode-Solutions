### 148. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Sort List

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/sort-list/)*</i>

Given the `head` of a linked list, return *the list after sorting it in **ascending order**.

给你链表的头结点 `head` ，请将其按 **升序** 排列并返回 **排序后的链表** 。

```python
# Example 1
head = [4,2,1,3] # Input
[1,2,3,4] # Output


# Example 2
head = [-1,5,3,4,0] # Input
[-1,0,3,4,5] # Output

# Example 3
head = [] # Input
[] 
```

#### Solution

```python
# extend the ListNode object
# this class can be reused for all problems related to ListNode
# 所有相关链表的问题都可以重用这个class

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

    @staticmethod
    def toLink(arr):
        # construct a ListNode object from a list
        # 将列表转化为链表
        head = None
        if len(arr) > 0:
            head = ListNode(arr[0])
            cur = head
            for i in range(1, len(arr)):
                cur.next = ListNode(arr[i])
                cur = cur.next
        return head

    @staticmethod
    def toList(head):
        # convert ListNode to list
        # 将链表转化为列表
        output = []
        while head is not None:
            output.append(head.val)
            head = head.next
        return output


class Solution:    
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        arr = ListNode.toList(head)
        arr.sort() # 链表转化为list之后可以直接用sort
        resultedLink = ListNode.toLink(arr)
        return resultedLink
```
