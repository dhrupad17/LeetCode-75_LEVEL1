# Backspace String Compare
---
- ## Question:
> Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.
> 
> Note that after backspacing an empty text, the text will continue empty.
---
- ## Example:
> Input: s = "ab#c", t = "ad#c"
> 
> Output: true
> 
> Explanation: Both s and t become "ac".
---
- ## Solution:
**Code :**
```C++
class Solution {
public:
    string berapbeng(string s)
    {
        stack<char>t;
        for(char c: s)
        {
            if(c=='#')
            {
                if(!t.empty())
                    t.pop();
            }
            else
                t.push(c);
        }
        string ans="";
        while(!t.empty())
        {
            ans+=t.top();
            t.pop();
        }
        return ans;
    }
    bool backspaceCompare(string s, string t) {
        string x1=berapbeng(s);
        string x2=berapbeng(t);
        return (x1==x2);
    }
};
