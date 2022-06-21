# Isomorphic Strings
---
- ## Question:
>Given two strings s and t, determine if they are isomorphic.
>
>Two strings s and t are isomorphic if the characters in s can be replaced to get t.
>
>All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.
---
- ## Example:
>Input: s = "egg", t = "add"
>
>Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int[] m=new int[512];
        for(int i=0;i<s.length();i++)
        {
            if(m[s.charAt(i)]!=m[t.charAt(i)+256])
                return false;
            m[s.charAt(i)]=m[t.charAt(i)+256]=i+1;
        }
        return true;
    }
}
