### 328. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Odd Even Linked List - 奇偶链表

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/odd-even-linked-list/)*</i>

Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return *the reversed list*.Given the `head` of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return *the reordered list*.

The **first** node is considered **odd**, and the **second** node is **even**, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in `O(1)` extra space complexity and `O(n)` time complexity.

-----------

给定单链表的头节点 head ，将所有索引为奇数的节点和索引为偶数的节点分别组合在一起，然后返回重新排序的列表。

第一个节点的索引被认为是 奇数 ， 第二个节点的索引为 偶数 ，以此类推。

请注意，偶数组和奇数组内部的相对顺序应该与输入时保持一致。

你必须在 O(1) 的额外空间复杂度和 O(n) 的时间复杂度下解决这个问题。



**Example 1**

![](https://assets.leetcode.com/uploads/2021/03/10/oddeven-linked-list.jpg)

```python
# Example 1
# Input
head = [1,2,3,4,5]
# Output [1,3,5,2,4]

```

**Example 2**

![](https://assets.leetcode.com/uploads/2021/03/10/oddeven2-linked-list.jpg)

```python
# Example 2
# Input
head = [2,1,3,5,6,4,7]
# Output [2,3,6,7,1,5,4]
```



#### Solution

Simply split the list into 2 lists: 1) list of nums in odd nodes and 2) list of nums in even nodes, and re-merge them.

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
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        arr = ListNode.toList(head)
        if arr:
            oddArr = [arr[i] for i in range(len(arr)) if i % 2 == 0]
            evenArr = [arr[i] for i in range(len(arr)) if i % 2 != 0]
            return ListNode.toLink(oddArr + evenArr)
        return None
```
