### 206. <span style="color:#08979c;background:#e6fffb;border-color:#87e8de;padding:1px 6px;border-radius:5px;">Easy</span> Reverse Linked List - 反转链表

<i style="float:right">Source: [LeetCode](https://leetcode.com/problems/reverse-linked-list/)</i>

Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

给你单链表的头节点 `head` ，请你反转链表，并返回反转后的链表。

```python
# Example 1
head = [1,2,3,4,5] # Input
# Output [5,4,3,2,1]


# Example 2
head = [1,2] # Input
# Output [2,1] 

# Example 3
head = [] # Input
# Output [] 
```

#### Solution

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
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        arr = ListNode.toList(head)
        if len(arr) < 1:
            return None
        output = []
        for i in range(len(arr)):
            output.append(arr[len(arr) - i - 1])
        return ListNode.toLink(output)
```
