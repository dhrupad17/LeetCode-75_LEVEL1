# N-ary Tree Preorder Traversal 
---
- ## Question:
>Given the root of an n-ary tree, return the preorder traversal of its nodes' values.
>
>Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples)
---
- ## Example:
![alt text](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)
>Input: root = [1,null,3,2,4,null,5,6]
>
>Output: [1,3,5,6,2,4]
---
- ## Solution:
**Code :**
```java
class Solution {
    ArrayList<Integer> ans=new ArrayList<>();
    public List<Integer> preorder(Node root) {
        if(root==null)
            return ans;
        ans.add(root.val);
        for(Node node: root.children)
        {
            preorder(node);
        }
        return ans;
    }
}
