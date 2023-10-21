# Intuition

Need to track the open and closing of brackets. One type of bracket cannot end without its open bracket counterpart.

# Approach

First, use `stack` to keep track of the open brackets. If a closing of bracket is found, then need to check if the last pushed element is its opening bracket counter part or not. If it's not, then the answer is `false` otherwise `pop` the last element in the stack. This cancels out that bracket sequence. Need to continue this until the end of the string. And at the end, if the stack is not empty, that means some open brackets are still there, which means corresponding closing brackets were not present. So, the answer is `false` then. Otherwise `true`.

# Complexity

- Time complexity: O(n)

- Space complexity: O(n)

# Code

```c++
class Solution {
public:
    bool isValid(string s) {
        int i;
        char last_open;
        stack <int> st;
        for (i = 0; i < s.size(); i++) {
            if(s[i] == '(' || s[i] == '[' || s[i] == '{') {
                st.push(s[i]);
            }
            else {
                if(!st.size()) return false;
                last_open = st.top();
                st.pop();
                if(last_open == '(' && s[i] == ')' || last_open == '{' && s[i] == '}' || last_open == '[' && s[i] == ']') continue;
                else return false;
            }
        }
        if(st.size()) return false;
        return true;
    }
};
```
