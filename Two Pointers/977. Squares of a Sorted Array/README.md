# Problem
Given an integer array `nums` sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

# Examples
Example 1
```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```

Example 2
```
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

# Constraints
- `1 <= nums.length <= 10^4`
- `-10^4 <= nums[i] <= 10^4`
- `nums` is sorted in non-decreasing order.

# Solutions
__C || `O(n)` || 112ms__

Since `nums` is sorted in non-decreasing order, the following sentences are true:
- If `nums[i], nums[i + 1] < 0`, then `nums[i]^2 > nums[i + 1]^2`.
- If `nums[i], nums[i + 1] > 0`, then `nums[i]^2 < nums[i + 1]^2`.
Hence either `nums[leftmost]^2` or `nums[rightmost]^2` is the biggest number in the resulting array.

```c
int* sortedSquares(int* nums, int numsSize, int* returnSize){
    int* res = malloc(numsSize * sizeof(int));
    *returnSize = numsSize;
    int l = 0, r = numsSize - 1, i = r;
    
    while (l <= r)
        if (nums[l] * nums[l] > nums[r] * nums[r])
            res[i--] = nums[l] * nums[l++];
        else
            res[i--] = nums[r] * nums[r--];
    
    return res;
}
```
