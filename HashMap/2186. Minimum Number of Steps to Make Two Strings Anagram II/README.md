# Problem
You are given two strings `s` and `t`. In one step, you can append any character to either `s` or `t`.

Return the minimum number of steps to make `s` and `t` anagrams of each other.

An anagram of a string is a string that contains the same characters with a different (or the same) ordering.

# Examples
Example 1
```
Input: s = "leetcode", t = "coats"
Output: 7
Explanation: 
- In 2 steps, we can append the letters in "as" onto s = "leetcode", forming s = "leetcodeas".
- In 5 steps, we can append the letters in "leede" onto t = "coats", forming t = "coatsleede".
"leetcodeas" and "coatsleede" are now anagrams of each other.
We used a total of 2 + 5 = 7 steps.
It can be shown that there is no way to make them anagrams of each other with less than 7 steps.
```

Example 2
```
Input: s = "night", t = "thing"
Output: 0
Explanation: The given strings are already anagrams of each other. Thus, we do not need any further steps.
```

# Constraints
- `1 <= s.length, t.length <= 2 * 10^5`
- `s` and `t` consist of lowercase English letters.

# Solutions
C || `O(n)` || 49ms
  
```c
int minSteps(char* s, char* t){
    int hmap[26] = {}, res = 0;
    
    while (*s) ++hmap[*s++ - 'a'];
    while (*t) --hmap[*t++ - 'a'];
    
    for (int i = 0; i < 26; ++i)
        res += (hmap[i] > 0) ? hmap[i] : -hmap[i];
    
    return res;
}
```
The code `while (*s)` is equivalent to `while (s[0] != '\0')`.
