# Intuition

By checking if all the letters of s is present in t anagram can be found.

# Approach

If the length of both strings are not equal, then there must be a letter missing which results **false**. Then by sorting both the strings and comparing them, if they match then the output is **true** or else its **false**

# Complexity

- Time complexity: O(NlogN + MlogM) where N and M is the length of s and t strings

- Space complexity: O(1)

# Code

```
class Solution {
public:
    bool isAnagram(string s, string t) {
      if (s.size() != t.size()) return false;
      else {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        if(s == t) return true;
        else return false;

      }
    }
};
```
