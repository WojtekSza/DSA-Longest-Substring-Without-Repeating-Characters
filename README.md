# DSA-Longest-Substring-Without-Repeating-Characters
Given a string s, find the length of the longest substring without repeating characters.
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```
```
from collections import defaultdict
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        ans=0
        left=0
        counts=defaultdict(int)
        for i in s: # Time cost O(n)
            counts[i]+=1
            while counts[i] >1: # Time cost O(n)
                l=s[left]
                counts[l]-=1
                if counts[l]==0:
                    del counts[l]
                left+=1
            ans=max(ans,len(counts.values())) #Space cost O(k)
        return ans
    '''
    Time cost in worst case each character will be visided twice therfore 2O(n) instead O(n^2) - loop in loop
    Space cost O(k) will be max unique value in substring o O(n)
    '''

```
