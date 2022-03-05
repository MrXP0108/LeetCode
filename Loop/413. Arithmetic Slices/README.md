# Problem
An integer array is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.

For example, `[1,3,5,7,9]`, `[7,7,7,7]`, and `[3,-1,-5,-9]` are arithmetic sequences.

Given an integer array `nums`, return the number of arithmetic subarrays of `nums`.

A subarray is a contiguous subsequence of the array.

# Examples
Example 1
```
Input: nums = [1,2,3,4]
Output: 3
Explanation: We have 3 arithmetic slices in nums: [1, 2, 3], [2, 3, 4] and [1,2,3,4] itself.
```

Example 2
```
Input: nums = [1]
Output: 0
```

# Constraints
- `1 <= nums.length <= 5000`
- `-1000 <= nums[i] <= 1000`

# Solutions
__C || `O(n)` || 0ms || 100%__

Since each subarray of an arithmetic array is also arithmetic, our main goal is to find longer arithmetic subarrays.

This can be simply done by checking if the current common difference `d` remains the same value as the previous one:
- If so, let `cur`, the size of the current subarray (let's call it `cur_longest` for now), plus one.
- If not, the current subarray is no longer arithmetic. We then add up the number of all subarrays of `cur_longest`, and reset `cur` and `d`.

```c
int numberOfArithmeticSlices(int* nums, int numsSize){
    if (numsSize < 3) return 0;
    
    int end = 1, d = nums[1] - nums[0], res = 0, cur = 2;
    
    while (++end < numsSize) {      
        if (nums[end] - nums[end - 1] != d) {
            d = nums[end] - nums[end - 1];
            if (cur > 2) {
                res += (cur - 1) * (cur - 2) / 2;
                cur = 2;
            }
        }
        else ++cur;
    }
    
    return (cur > 2) ? (res + (cur - 1) * (cur - 2) / 2) : res;
}
```
