# Find All Anagrams in a String
---
- ## Question:
> Given two strings s and p, return an array of all the start indices of p's anagrams in s. You may return the answer in any order.
> 
> An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
---
- ## Example:
> Input: s = "cbaebabacd", p = "abc"
> 
> Output: [0,6]
> 
> Explanation:
> 
> The substring with start index = 0 is "cba", which is an anagram of "abc".
> 
> The substring with start index = 6 is "bac", which is an anagram of "abc".
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        int f1[]=new int[26];
        int f2[]=new int[26];
        List<Integer> ans=new ArrayList<>();
        if(s.length()<p.length())
            return ans;
        for(int i=0;i<p.length();i++)
        {
            f1[s.charAt(i)-'a']++;
            f2[p.charAt(i)-'a']++;
        }
        int start=0;
        int end=p.length();
        if(Arrays.equals(f1,f2))
            ans.add(start);
        while(end<s.length())
        {
            f1[s.charAt(start)-'a']--;
            f1[s.charAt(end)-'a']++;
            if(Arrays.equals(f1,f2))
            {
                ans.add(start+1);
            }
            start++;
            end++;
        }
        return ans;
    }
}
