### 206. <span style="color:#08979c;background:#e6fffb;border-color:#87e8de;padding:1px 6px;border-radius:5px;">Easy</span> Reverse Linked List - 链表的中间结点

<i style="float:right">Source: [LeetCode](https://leetcode.com/problems/reverse-linked-list/)</i>

Given the `head` of a singly linked list, return *the middle node of the linked list*.

If there are two middle nodes, return **the second middle** node.

给你单链表的头结点 `head` ，请你找出并返回链表的中间结点。

如果有两个中间结点，则返回第二个中间结点。

```python
# Example 1
head = [1,2,3,4,5] # Input
# Output [3,4,5] 

# Example 2
head = [1,2,3,4,5,6] # Input
# Output [4,5,6] 
```

#### Solution

Similar to finding the median of a list of numbers. We can locate the index of the middle node using `//` floor division. 类似于找中位数，我们用向下整除法得到中间位置就好。

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
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        arr = ListNode.toList(head)
        if len(arr) < 1:
            return None
        mid = arr[len(arr) // 2:]
        return ListNode.toLink(mid)
```
