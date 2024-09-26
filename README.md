# Count-Different-Palindromic-Subsequences

Given a string s, return the number of different non-empty palindromic subsequences in s. Since the answer may be very large, return it modulo 109 + 7.
A subsequence of a string is obtained by deleting zero or more characters from the string.
A sequence is palindromic if it is equal to the sequence reversed.
Two sequences a1, a2, ... and b1, b2, ... are different if there is some i for which ai != bi.

Constraints:
1 <= s.length <= 1000
s[i] is either 'a', 'b', 'c', or 'd'.

class Solution:
    def countPalindromicSubsequences(self, s: str) -> int:

        @lru_cache(None)
        def dp(left: int, rght: int, res = 0):

            for ch in 'abcd':

                l, r = s.find(ch,left,rght), s.rfind(ch,left,rght)
                
                res+= 0 if l==-1 else 1 if l==r else dp(l+1,r)+2

            return res %1_000_000_007

        return dp(0,len(s))
