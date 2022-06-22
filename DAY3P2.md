# Reverse Linked List
---
- ## Question:
>Given the head of a singly linked list, reverse the list, and return the reversed list.
>
![alt text](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)
---
- ## Example
>Input: head = [1,2,3,4,5]
>
>Output: [5,4,3,2,1]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null||head.next==null)
            return head;
        ListNode nextnode=head.next;
        ListNode newnode=reverseList(nextnode);
        nextnode.next=head;
        head.next=null;
        return newnode;
    }
}
