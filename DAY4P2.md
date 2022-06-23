# Linked List Cycle II
---
- ## Question:
>Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.
>
>There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.
---
- ## Example:
![ALT TEXT](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)
>Input: head = [3,2,0,-4], pos = 1
>
>Output: tail connects to node index 1
>
>Explanation: There is a cycle in the linked list, where tail connects to the second node.
---
- ## Solution:
**Code :**
```java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode fast,slow;
        slow=head;
        fast=head;
        while(fast!=null && fast.next!=null)
        {
            slow=slow.next;
            fast=fast.next.next;
            if(slow==fast)
            {
                ListNode slow2=head;
                while(slow2!=slow)
                {
                    slow=slow.next;
                    slow2=slow2.next;
                }
                return slow;
            }
        }
        return null;
    }
}
