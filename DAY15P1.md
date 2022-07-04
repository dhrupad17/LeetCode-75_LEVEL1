# Last Stone Weight
---
- ## Question:
> You are given an array of integers stones where stones[i] is the weight of the ith stone.
> 
> We are playing a game with the stones. On each turn, we choose the heaviest two stones and smash them together. Suppose the heaviest two stones have weights x and y with x <= y. The result of this smash is:
> 
>- If x == y, both stones are destroyed, and
>- If x != y, the stone of weight x is destroyed, and the stone of weight y has new weight y - x.
>
> At the end of the game, there is at most one stone left.
> 
> Return the weight of the last remaining stone. If there are no stones left, return 0
---
- ## Example:
> Input: stones = [2,7,4,1,8,1]
> 
> Output: 1
---
- ## Solution:
**Code :**
```java
class Solution {
    public int lastStoneWeight(int[] stones) {
	var maxHeap = new PriorityQueue<Integer>(Collections.reverseOrder());
	
	for (var stone : stones)
		maxHeap.add(stone);

	while (maxHeap.size() > 1)
		maxHeap.offer(maxHeap.poll() - maxHeap.poll());
		
	return maxHeap.poll();
}
}
