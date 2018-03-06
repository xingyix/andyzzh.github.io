## Question:

Reverse Words in a String II

Given an input string, reverse the string word by word. A word is defined as a sequence of non-space characters.

The input string does not contain leading or trailing spaces and the words are always separated by a single space.

For example,
Given s = "`the sky is blue`",
return "`blue is sky the`".

Could you do it *in-place* without allocating extra space?

Related problem: [Rotate Array](https://leetcode.com/problems/rotate-array/)

**Update (2017-10-16):**
We have updated the function signature to accept a `character array`, so please **reset to the default code definition** by clicking on the reload button above the code editor. Also, **Run Code** is now available!

---

## Thoughts:

* Two pointer swapping methods are not likely to work since words have different length and we can not use an extra char array to store temp. Without storing temp word swapping is impossible.
* Now consider first reverse the whole char array
  * "the sky is blue" => "bulb is yks eht"
  * One pass - O(n)
* The reverse each word
  * One pass - O(n)
* In total we need two passes without extra space
  * O(n) in time
  * No space is used

---

# Code:

```java
class Solution {
    public void reverseWords(char[] str) {
        // 1. reverse the whole char array
        reverse(str, 0, str.length-1);
        
        // 2. reverse each word
        int wordStart = 0;
        for (int i=0; i< str.length; i++){
            if (str[i] == ' '){
                reverse(str,wordStart, i-1);
                wordStart = i+1;
            }
        }
        // 3. reverse the last word
        reverse(str, wordStart, str.length-1);
    }
    public void reverse(char[] s, int i, int j){
        while(i<j){
            char temp = s[i];
            s[i]=s[j];
            s[j]=temp;
            i++;
            j--;
        }
    }
}
```

