# Statement

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

> Input: nums = [100,4,200,1,3,2] \
> Output: 4\
> Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

# Intuition

By using `unordered_set`, need to check the consecutive sequence.

# Approach

This problem is simple if we use `sorting`. But as the requirement, it has to be done on `O(n)` time. So, `unordered_set` is used because every operation in `unordered_set` takes average of `O(1)`.

So, in the `hash` of `unordered_set` we need to check if a element is the starting of a sequence or not. This can be done by checking if `number-1` is present for `number` in the array. If it is present, then that number cannot be the start of a sequence.
Otherwise, we follow that number by incrementing that and searching through the array.

# Complexity

- Time complexity: `O(n)`

- Space complexity: `O(n)`

# Code

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int count = 1, mx = 1, next;
        unordered_set <int> hash(nums.begin(), nums.end());
        if(hash.empty()) return 0;
        for(int it: hash) {
          if(hash.find(it-1) == hash.end()) {
            next = it+1;
            while(hash.find(next) != hash.end()) {
              count++;
              next++;
            }
            mx = max(mx, count);
            count = 1;
          }
        }
        return mx;
    }
};
```
