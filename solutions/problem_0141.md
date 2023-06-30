### 141. <span style="color:#08979c;background:#e6fffb;border-color:#87e8de;padding:1px 6px;border-radius:5px;">Easy</span> Linked List Cycle - 环形链表

<i style="float:right">Source: [LeetCode](https://leetcode.com/problems/linked-list-cycle/)</i>

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` *if there is a cycle in the linked list*. Otherwise, return `false`.

-----------------------------------

给你一个链表的头节点 head ，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。注意：pos 不作为参数进行传递 。仅仅是为了标识链表的实际情况。

如果链表中存在环 ，则返回 true 。 否则，返回 false 。

**Example 1**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

**Example 2**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

**Example 3**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

```python
# Example 1
# Input
head = [3,2,0,-4]
pos = 1
# Output True

# Example 2
# Input
head = [1,2]
pos = 0
# Output True

# Example 3
# Input
head = [1]
pos = -1
# Output False
```

#### Solution

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        temp = []
        while head:
            if head in temp:
                return True
            temp.append(head)
            head = head.next
        return False
```
