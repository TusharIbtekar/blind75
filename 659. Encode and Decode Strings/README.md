# Intuition

Need to add a string after every word to encode it and remove it to decode it.

# Approach

We can encode the string by adding `:;` to the end of a word. And for decoding, we need to extract the word by removing the `:;` and make a list exactly like the given input which was given in encode.
Encoding is pretty straight forward. For decoding, we can keep a `temp` variable to extract each word between `:;` and push it to the `answer` vector.

# Complexity

- Time complexity: `O(n)`

- Space complexity: `O(1)`

# Code

```c++
class Solution {
public:
    string encode(vector<string> &strs) {
        int i;
        string encoded = strs[0];
        for(i = 1; i < strs.size(); i++) {
            encoded += ":;" + strs[i];
        }
        return encoded;
    }

    vector<string> decode(string &str) {
        int i;
        vector <string> strs;
        string temp = "";
        for(i = 0; i < str.length(); i++) {
            if(str[i] == ':' && str[i+1] == ';' && i < str.length()) {
                i++;
                strs.push_back(temp);
                temp = "";
            }
            else {
                temp += str[i];
            }
        }
        strs.push_back(temp);
        return strs;
    }
};
```
