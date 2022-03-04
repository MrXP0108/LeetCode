# Problem
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool isBadVersion(version)` which returns whether `version` is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

# Examples
Example 1
```
Input: n = 5, bad = 4
Output: 4
Explanation:
call isBadVersion(3) -> false
call isBadVersion(5) -> true
call isBadVersion(4) -> true
Then 4 is the first bad version.
```

Example 2
```
Input: n = 1, bad = 1
Output: 1
```

# Constraints
```
1 <= bad <= n <= 231 - 1
```

# Solutions
C, C# || `O(log n)` || 0ms || 100%
  
```c
int firstBadVersion(int n) {
    if (isBadVersion(1)) return 1;
    
    int first = 1, last = n, middle;
    
    while (first <= last) {
        middle = (int)((long)first + (long)last >> 1);
        
        if (isBadVersion(middle) && !isBadVersion(middle - 1))
            return middle;
        else if (isBadVersion(middle))
            last  = middle - 1;
        else
            first = middle + 1;
    }
    
    return -1;
}
```
