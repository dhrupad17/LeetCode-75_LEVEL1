# Decode String
---
- ## Question:
> Given an encoded string, return its decoded string.
> 
> The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.
> 
> You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there will not be input like 3a or 2[4].
> 
> The test cases are generated so that the length of the output will never exceed 105.
---
- ## Example:
> Input: s = "3[a]2[bc]"
> 
> Output: "aaabcbc"
---
- ## Solution:
**Code :**
```java
class Solution {
    public String decodeString(String s) {
        
        Stack<Character> stack = new Stack<>();
        
        for(char c : s.toCharArray())
        {
            if(c != ']') 
                stack.push(c); //push everything but ]
            
            else 
            {
                //step 1: 
                    //if you find a closing ] then 
                   //retrieve the string it encapsulates
                
                StringBuilder sb = new StringBuilder();
                while(!stack.isEmpty() && Character.isLetter(stack.peek()))
                    sb.insert(0, stack.pop());
                
                String sub = sb.toString(); //this is the string contained in [ ]
                stack.pop(); //Discard the '[';
                
                
                //step 2: 
                    //after that get the number of
                  // times it should repeat from stack
                    
                sb = new StringBuilder();
                while(!stack.isEmpty() && Character.isDigit(stack.peek()))
                    sb.insert(0, stack.pop());
                    
                int count = Integer.valueOf(sb.toString()); //this is the number
                
                
                //step 3: 
                    //repeat the string within the [ ] count 
                  //number of times and push it back into stack
                
                while(count > 0)
                {
                    for(char ch : sub.toCharArray())  
                        stack.push(ch);
                    count--;
                }
            }
        }
        
      //final fetching and returning the value in stack 
        StringBuilder retv = new StringBuilder();
        while(!stack.isEmpty())
            retv.insert(0, stack.pop());

        return retv.toString();
    }
}
