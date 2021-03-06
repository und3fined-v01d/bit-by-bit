---
title: "Strobogrammatic Number"
date: "2020-08-20T16:43:51.354Z"
category: ["google"]
description: "Write a function to determine if a number is strobogrammatic."
emoji: "😄"
difficulty: "easy"
---

## Strobogrammatic Number

A strobogrammatic number is a number that looks the same when **rotated 180 degrees** (looked at upside down).

Write a function to determine if a number is strobogrammatic. The number is represented as a string.

For example, the numbers `"69"`, `"88"`, and `"818"` are all strobogrammatic.

## C++

```cpp
class Solution {
public:
    bool isStrobogrammatic(string s) {
        int n = s.size();

        // Map storing valid possible characters
        // that can appear in strobogrammatic
        // numbers
        unordered_map <char, char> match = {
            {'0', '0'},
            {'1', '1'},
            {'8', '8'},
            {'6', '9'},
            {'9', '6'}
        }

        // Use the two-pointer trick to
        // compress down to the center
        int start = 0, end = n-1;

        while(start <= end) {
            // If keys don't match return
            // false
            if(match(s[start]) != s[end])
                return false;

            start++;
            end--;
        }

        return true;
    }
}
```
