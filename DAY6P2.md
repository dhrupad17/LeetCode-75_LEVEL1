# Binary Tree Level Order Traversal
---
- ## Question:
>Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).
---
- ## Example:
![ALT TEXT](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)
>Input: root = [3,9,20,null,null,15,7]
>
>Output: [[3],[9,20],[15,7]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
		List<List<Integer>> output = new ArrayList<>();
		levelOrderHelper(output, root, 0);
		return output;
	}
	
	public void levelOrderHelper(List<List<Integer>> output, TreeNode root, int level) {
		if (root == null) {
            return;
        } else {
            if (level >= output.size()) {
                output.add(new ArrayList<>());
            }   
            output.get(level).add(root.val);
            levelOrderHelper(output, root.left, level + 1);
            levelOrderHelper(output, root.right, level + 1);
        }
	}
}
