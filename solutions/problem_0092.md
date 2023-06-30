### 92. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Reverse Linked List II - 反转链表 II

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/reverse-linked-list-ii/)*</i>

Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return *the reversed list*.

-----------

给你单链表的头指针 head 和两个整数 left 和 right ，其中 left <= right 。请你反转从位置 left 到位置 right 的链表节点，返回 反转后的链表 。

**Example 1**

![](https://assets.leetcode.com/uploads/2021/02/19/rev2ex2.jpg)

```python
# Example 1
# Input
head = [1,2,3,4,5]
left = 2
right = 4
# Output [1,4,3,2,5]

# Example 2
# Input
head = [5]
left = 1
right = 1
# Output None
```

#### Solution

What I tried to do here is to save the selected items, and replace them with the reversed list of selected items.

这里我们可以先存一下选中的数字，对数字做一个反转，然后替代原先列表里面的数字。

```python
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
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        arr = ListNode.toList(head)
        if arr:
            start, end = left - 1, right
            arrSel = arr[start: end]
            arrLen = right - left
            # reverse selected nums
            arr[start:end] = [arrSel[arrLen - i] for i in range(arrLen + 1)]
            return ListNode.toLink(arr)
        return None
```
