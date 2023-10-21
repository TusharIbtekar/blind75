# Intuition

By calculating the products of the array and then dividing it by current element, the answer can be found.

# Approach

First, need to calculate the product of the elements of the array. There are two observations:

- if the array contains more than two zeros, then every element of the `ans` array will be zero.
- if only one of the element is zero, then every element except that will be zero.
- if there is no zero, then simply dividing the product with current element and putting it in `ans` array does the trick.

# Complexity

- Time complexity: O(n)

- Space complexity: O(n)

# Code

```c++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int sum = 1, i, zero = 0;
        vector<int> ans(nums.size(), 0);
        for(i = 0; i < nums.size(); i++) {
          if(nums[i]) {
            sum *= nums[i];
          }
          else zero++;
        }
        if(zero > 1) {
          return ans;
        }
        for(i = 0; i < nums.size(); i++) {
          if(zero) {
            if(nums[i]) {
              ans[i] = 0;
            }
            else ans[i] = sum;
            continue;
          }
          if(nums[i])
            ans[i] = sum/nums[i];
          else {
            ans[i] = sum;
          }
        }
        return ans;
    }
};
```
