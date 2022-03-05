# Problem
You are given two strings `s1` and `s2` of equal length. A string swap is an operation where you choose two indices in a string (not necessarily different) and swap the characters at these indices.

Return `true` if it is possible to make both strings equal by performing at most one string swap on exactly one of the strings. Otherwise, return `false`.

# Examples
Example 1
```
Input: s1 = "bank", s2 = "kanb"
Output: true
Explanation: For example, swap the first character with the last character of s2 to make "bank".
```

Example 2
```
Input: s1 = "attack", s2 = "defend"
Output: false
Explanation: It is impossible to make them equal with one string swap.
```

Example 3
```
Input: s1 = "kelb", s2 = "kelb"
Output: true
Explanation: The two strings are already equal, so no string swap operation is required.
```

# Constraints
- `1 <= s1.length, s2.length <= 100`
- `s1.length == s2.length`
- `s1` and `s2` consist of only lowercase English letters.

# Solutions
__C || `O(n)` || 0ms || 100%__

By observation, there are only two cases that return `true`:
1. `s1 == s2` without alternation.
2. `s1 == s2` after swapping two characters of `s1`.
So we only need to check if either of these is true.

```c
bool areAlmostEqual(char* s1, char* s2){
    // check case 1
    if (strcmp(s1, s2) == 0) return true;
    
    // check case 2
    char diff1_1 = ' ', diff1_2 = ' ', diff2_1 = ' ', diff2_2 = ' ';
    while (*s1) {
        if (*s1 != *s2) {
            // case 2 will not be complied if there are more than two differences
            if (diff1_1 != ' ' && diff1_2 != ' ') return false;
            
            if (diff1_1 == ' ') {
                diff1_1 = *s1;
                diff2_1 = *s2;
            }
            else {
                diff1_2 = *s1;
                diff2_2 = *s2;
            }
        }
        s1++; s2++;
    }
    // case 2 will not be complied if there is only one difference
    if (diff1_2 == ' ') return false;
    
    return (diff1_1 == diff2_2 && diff1_2 == diff2_1);
}
```
