### 142. <span style="color:#d46b08;background:#fff7e6;border-color:#ffd591;padding:1px 6px;border-radius:5px">Medium</span> Linked List Cycle II - 环形链表 II

<i style="float:right">*Source: [LeetCode](https://leetcode.com/problems/linked-list-cycle-ii/)*</i>

Given the `head` of a linked list, return *the node where the cycle begins. If there is no cycle, return* `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to (**0-indexed**). It is `-1` if there is no cycle. **Note that** `pos` **is not passed as a parameter**.

-----------

给定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。不允许修改 链表。

**Example 1**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

**Example 2**

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

```python
# Example 1
# Input
head = [3,2,0,-4]
pos = 1
# Output 1

# Example 2
# Input
head = [1,2]
pos = 0
# Output None
```

#### Solution

Similar to [141. Linked List Cycle](solutions/problem_0141.md)

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        temp = []
        while head:
            if head in temp:
                return head
            temp.append(head)
            head = head.next
        return None
```
