# Intuition

Grouping together the list of anagrams which contains the same letters in a word.

# Approach

This can be done with hashmaps. By iterating through every string and sorting that string will make a general form of that anagram. Then making it the key of hashmap, after inserting all the strings which generalized form matches with this one, a group is created.
Example:

```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Hashmap: [
"aet": ["eat", "tea", "ate"],
"ant": ["tan", "nat"],
"abt": ["bat"],
]
```

With this, the list is created.

# Complexity

- Time complexity: O(n\*m) where n is the size of input and m is the average length of the strings.

- Space complexity: O(n)

# Code

```c++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> ans;
        map<string, vector<string>> freq;
        vector<string> index;
        string temp;
        int i;
        for (i = 0; i < strs.size(); i++) {
            temp = strs[i];
            sort(temp.begin(), temp.end());
            if(freq[temp].empty()) {
                index.push_back(temp);
                // cout << temp << endl;
            }
            freq[temp].push_back(strs[i]);

        }
        for(i = 0; i < index.size(); i++) {
            ans.push_back(freq[index[i]]);
        }
        return ans;
    }
};
```
