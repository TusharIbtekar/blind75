# Intuition

From the given `nums`, need to find out the first `k` number of elements that appears the most. Simply, need to print `k` elements with most frequency.

# Approach

First, need to find the frequency map(which element appears how many times). For this, `map` can be used to create a hashmap to make the frequency map.

```
Input: nums = [1,1,1,2,2,3], k = 2
hash:
[key: frequency] = [1:3, 2:2, 3:1]
```

As k elements with maximum number of appearances need to be shown, the frequency and elements can be paired to preserve elements according to its frequency before sorting, otherwise the elements will be lost.

```
freq_index_pair: [(3, 1), (2, 2), (1, 3)]
```

Now soring it gives the orders accordingly, just taking first k elements will do the trick.

# Complexity

- Time complexity: `O(nlog(n))`

- Space complexity: `O(n)`
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code

```c++
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        int i;
        map <int, int> hash;
        vector <pair<int, int>> freq_index_pair;
        vector <int> ans, freq;

        for(i = 0; i < nums.size(); i++) {
            hash[nums[i]]++;
        }

        for(i = 0; i < nums.size(); i++) {
            if(hash[nums[i]]) {
                freq_index_pair.push_back(make_pair(hash[nums[i]], nums[i]));
                hash[nums[i]] = 0;
            }
        }
        sort(freq_index_pair.begin(), freq_index_pair.end(), greater <> ());

        for(i = 0; i < freq_index_pair.size() && k; i++) {
            ans.push_back(freq_index_pair[i].second);
            k--;
        }

        return ans;

    }
};
```
