---
title: Longest Word in a Dictionary
date: 2020-09-01T01:31:12.929Z
description: Given a list of strings words representing an English Dictionary,
  find the longest lexicographically lowest word in words that can be built one
  character at a time by other words in words.
difficulty: easy
emoji: 😄
category:
  - google
---
## [Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)

Given a list of strings `words` representing an English Dictionary, find the longest word in `words` that can be built one character at a time by other words in `words`. If there is more than one possible answer, return the longest word with the smallest lexicographical order.

If there is no answer, return the empty string.

Example 1:

**Input**:  `words = ["w","wo","wor","worl", "world"]`

**Output**: `"world"`

**Explanation**: 
The word `"world"` can be built one character at a time by `"w"`, `"wo"`, `"wor"`, and `"worl"`.

Example 2:

**Input**: `words = ["a", "banana", "app", "appl", "ap", "apply", "apple"]`

**Output**: `"apple"`

**Explanation**: Both `"apply"` and `"apple"` can be built from other words in the dictionary. However, `"apple"` is lexicographically smaller than `"apply"`.

**Note:**

* All the strings in the input will only contain lowercase letters.
* The length of `words` will be in the range `[1, 1000]`.
* The length of `words[i]` will be in the range `[1, 30]`.

## C++

```cpp
class Solution {
public:
    string longestWord(vector<string>& words) {
        set<string> dict;
        
        for(auto word: words)
            dict.insert(word);
        
        string longest = "";
        
        for(auto word: dict) {
            string prefix = "";
            
            for(auto ch: word) {
                prefix += ch;
                
                if(dict.find(prefix) == dict.end())
                    break;
            }
            
            if(longest.size() < prefix.size() && dict.find(prefix) != dict.end())
                longest = prefix;
        }
        
        return longest;
    }
};
```