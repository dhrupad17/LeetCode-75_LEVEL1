# Top K Frequent Words
---
- ## Question:
> Given an array of strings words and an integer k, return the k most frequent strings.
> 
> Return the answer sorted by the frequency from highest to lowest. Sort the words with the same frequency by their lexicographical order.
---
- ## Example:
> Input: words = ["i","love","leetcode","i","love","coding"], k = 2
> 
> Output: ["i","love"]
> 
> Explanation: "i" and "love" are the two most frequent words.
>Note that "i" comes before "love" due to a lower alphabetical order
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        Map<String, Integer> map = new HashMap<>();
        for (String s: words)
            map.put(s, map.getOrDefault(s, 0)+ 1);
        Queue<String> q = new PriorityQueue<>((w1, w2) -> map.get(w1).equals(map.get(w2)) ?
                w2.compareTo(w1) : map.get(w1) - map.get(w2));
        for (String word: map.keySet()){
            q.add(word);
            if (q.size() > k) q.poll();
        }
        List<String> result = new ArrayList<>();
        while (!q.isEmpty())
            result.add(q.poll());
        Collections.reverse(result);
        return result;
    }
}
