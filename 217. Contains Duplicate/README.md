# Intuition

Need to check for repetitive elements

# Approach

STL set takes only the distinct numbers and sorts it. So, by using set and then comparing with the size of the given vector, solution can be acquired.

# Complexity

- Time complexity: O(nlog(n))

- Space complexity: O(n)

# Code

```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int>st;
        for(int i = 0; i < nums.size(); i++) {
          st.insert(nums[i]);
        }
        return st.size() != nums.size();
    }
};
```
