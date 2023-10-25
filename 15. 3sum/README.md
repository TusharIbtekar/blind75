# Statement

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

> Input: nums = [-1,0,1,2,-1,-4] \
> Output: [[-1,-1,2],[-1,0,1]] \
> Explanation: \
> nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0. \
> nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0. \
> nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0. \
> The distinct triplets are [-1,0,1] and [-1,-1,2]. \
> Notice that the order of the output and the order of the triplets does not matter.

# Intuition

Can be done with `Two Pointer` approach where tracking each element and checking each of them manually will lead to the solution.

# Approach

First, need to `sort` the array to ensure that the each triplet is in a non-descending array. Then going through each of the elements to adding them to see if it leads to `0` or not.

To avoid duplicate triplets, we can take only one even if it is a repitative element per iteration. Because the array is already `sorted`, duplicate elements will stay together. So, checking it will be a piece of cake.

To explain further, for each element index `i`, we need to check from it's next element, `j`. To, find triplets, we will need another pointer, `k` which will run from the end. Now, if we find `0`, that is a valid triplet and will be pushed in the `ans`. But if not, then if it is less than 0, then we will need a larger value, so, we increase `j` (Because it is sorted in non-descending order). if it is more than `0`, then we increase `k`, because we need to lower the sum to make it `0`.

# Complexity

- Time complexity: `O(n^2)`

- Space complexity: `O(n)`

# Code

```c++
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector <vector<int>> ans;
        int i, j, temp, k;
        sort(nums.begin(), nums.end());

        for(i = 0; i < nums.size(); i++) {
            if(i > 0 && nums[i] == nums[i-1]) continue; // to avoid duplicate triplets
            j = i+1;
            k = nums.size()-1;
            while(j < k) {
                temp = nums[i] + nums[j] + nums[k];
                if(temp == 0) {
                    ans.push_back({nums[i], nums[j], nums[k]});
                    j++;
                    k--;
                    // to avoid duplicate triplets
                    while(j < k && nums[j-1] == nums[j]) j++;
                    while(j < k && nums[k+1] == nums[k]) k--;
                }
                else if(temp > 0) k--;
                else j++;
            }
        }
        return ans;
    }
};
```
