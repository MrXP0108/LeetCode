# Problem
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

# Examples
Example 1
```
Input: s = "anagram", t = "nagaram"
Output: true
```

Example 2
```
Input: s = "rat", t = "car"
Output: false
```

# Constraints
- `1 <= s.length, t.length <= 5 * 10^4`
- `s` and `t` consist of lowercase English letters.

# Solutions
__C || `O(n)` || 0ms || 100%__

```c
bool isAnagram(char* s, char* t){
    int hmap[26] = {};
    
    while (*s && *t) {
        ++hmap[*s++ - 'a'];
        --hmap[*t++ - 'a'];
    }
    if (*s || *t) return false;
    
    for (int i = 0; i < 26; ++i)
        if (hmap[i] != 0) return false;
    
    return true;
}
```