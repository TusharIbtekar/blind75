# Intuition

Need to find out the indexes of two numbers which forms a given number(target) when added.

# Approach

The solution can be reached with hashing the indexes of the elements of the array. With this, we can know any element's index with `O(1)` complexity. Now, by taking a elements and substracting it from the target, we check if the number exists or not. If it does, then we can easily find out its index from the hash map.

```
Input: nums = [1,3,4,2], target = 6
Output: [2,3]
Explanation:
hash_map:
[key: value] = [1:0, 3:1, 4:2, 2:3]
rem = target - nums[2] = 6 - 4 = 2
So, hash_map[2] has index 3, and hash_map[4] has index 2.

```

# Complexity

- Time complexity: O(n) where n is the length of the input array.

- Space complexity: O(n)

# Code

```
class Solution {
public:
  vector<int> twoSum(vector<int>& nums, int target) {
      map<int, int> mp;
      vector<int> ans;
      int i, rem;
      for(i = 0; i < nums.size(); i++) {
        mp[nums[i]] = i;
      }
      for(i = 0; i < nums.size(); i++) {
        rem = target - nums[i];
        if(mp[rem] && i != mp[rem]) {
          ans.push_back(i);
          ans.push_back(mp[rem]);
          break;
        }
      }
      return ans;
  }
};
```
