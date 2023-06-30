### 160. <span style="color:#08979c;background:#e6fffb;border-color:#87e8de;padding:1px 6px;border-radius:5px;">Easy</span> Intersection of Two Linked Lists - 相交链表

<i style="float:right">Source: [LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/)</i>

Given the heads of two singly linked-lists `headA` and `headB`, return *the node at which the two lists intersect*. If the two linked lists have no intersection at all, return `null`.

给你两个单链表的头节点 headA 和 headB ，请你找出并返回两个单链表相交的起始节点。如果两个链表不存在相交节点，返回 null 。

图示两个链表在节点 c1 开始相交：

![](https://assets.leetcode.com/uploads/2021/03/05/160_statement.png)

The test cases are generated such that there are no cycles anywhere in the entire linked structure.

**Note** that the linked lists must **retain their original structure** after the function returns.

**Custom Judge:**

The inputs to the **judge** are given as follows (your program is **not** given these inputs):

- `intersectVal` - The value of the node where the intersection occurs. This is `0` if there is no intersected node.
- `listA` - The first linked list.
- `listB` - The second linked list.
- `skipA` - The number of nodes to skip ahead in `listA` (starting from the head) to get to the intersected node.
- `skipB` - The number of nodes to skip ahead in `listB` (starting from the head) to get to the intersected node.

The judge will then create the linked structure based on these inputs and pass the two heads, `headA` and `headB` to your program. If you correctly return the intersected node, then your solution will be **accepted**.

**Example 1**

![](https://assets.leetcode.com/uploads/2021/03/05/160_example_1_1.png)

**Example 2**

![](https://assets.leetcode.com/uploads/2021/03/05/160_example_2.png)

```python
# Example 1
# Input
listA = [4,1,8,4,5]
listB = [5,6,1,8,4,5]
# Output Intersected at '8'

# Example 2
listA = [1,9,1,2,4]
listB = [3,2,4]
# Output Intersected at '2'
```

#### Solution

注意，linked list在python里面不构成环，所以本地好难测试哦。但是这个solution是可以通过的。

```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        a, b = headA, headB
        while a != b:
            if a:
                a = a.next 
            else:
                a = headB

            if b:
                b = b.next
            else:
                b = headA
        return a
```
