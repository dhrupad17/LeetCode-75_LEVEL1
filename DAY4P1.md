# Middle of the Linked List
---
- ## Question:
>Given the head of a singly linked list, return the middle node of the linked list.
>
>If there are two middle nodes, return the second middle node.
---
- ## Example:
![alt text](https://assets.leetcode.com/uploads/2021/07/23/lc-midlist1.jpg)
>Input: head = [1,2,3,4,5]
>
>Output: [3,4,5]
>
>Explanation: The middle node of the list is node 3.
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode p1,p2;
        p1=head;
        p2=head;
        while(p2!=null && p2.next!=null)
        {
            p1=p1.next;
            p2=p2.next.next;
        }
        return p1;
    }
}
