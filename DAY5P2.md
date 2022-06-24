# Longest Palindrome
---
- ## Question:
>Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.
>
>Letters are case sensitive, for example, "Aa" is not considered a palindrome here.
---
- ## Example:
>Input: s = "abccccdd"
>
>Output: 7
>
>Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int longestPalindrome(String s) {
        if(s==null || s.length()==0)
            return 0;
        int count=0;
        HashSet<Character> hs=new HashSet<>();
        for(int i=0;i<s.length();i++)
        {
            if(hs.contains(s.charAt(i)))
            {
                hs.remove(s.charAt(i));
                count++;
            }
            else
            {
                hs.add(s.charAt(i));
            }
                
        }
        if(hs.isEmpty())
            return count*2;
        return count*2+1;
    }
}
