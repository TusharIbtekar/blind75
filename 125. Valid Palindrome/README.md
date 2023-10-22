# Statement

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

> Input: s = "A man, a plan, a canal: Panama"\
> Output: true\
> Explanation: "amanaplanacanalpanama" is a palindrome.

# Intuition

Need to check if the string is palindrome after removing the special characters.

# Approach

Remove the special characters and convert the capitals to small letter. Then match each characters from start and end.

# Complexity

- Time complexity: `O(n)`

- Space complexity: `O(n)`

# Code

```c++
class Solution {
public:
    bool isPalindrome(string s) {
        string filtered = "";
        int i;
        for(i = 0; i < s.length(); i++) {
            if('a' <= s[i] && 'z' >= s[i] || '0' <= s[i] && '9' >= s[i]) filtered += s[i];
            else if('A' <= s[i] && 'Z' >= s[i]) filtered += s[i] + 32;
        }
        int j = filtered.length()-1;
        if(j < 1) return true;
        for(i = 0;;i++, j--) {
            if(i >= j) return true;
            if(filtered[i] != filtered[j]) {
                return false;
            }

        }
    }
};
```
