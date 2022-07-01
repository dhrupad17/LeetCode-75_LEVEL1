# Longest Repeating Character Replacement
---
- ## Question:
> You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.
> 
> Return the length of the longest substring containing the same letter you can get after performing the above operations.
---
- ## Example:
> Input: s = "ABAB", k = 2
> 
> Output: 4
> 
> Explanation: Replace the two 'A's with two 'B's or vice versa.
---
- ## Solution:
**Code :**
```java
class Solution {
     public int characterReplacement(String s, int k) {
        int len = s.length();
        int[] count = new int[26];
        int start = 0, maxCount = 0, maxLength = 0;
        for (int end = 0; end < len; end++) {
            maxCount = Math.max(maxCount, ++count[s.charAt(end) - 'A']);
            while (end - start + 1 - maxCount > k) {
                count[s.charAt(start) - 'A']--;
                start++;
            }
            maxLength = Math.max(maxLength, end - start + 1);
        }
        return maxLength;
    }
}
