Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without repeating characters.



Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.


Solution:
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character>set=new HashSet<>();
        int res=0,left=0;
        for(int i=0;i<s.length();i++) {
            while(set.contains(s.charAt(i))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(i));
            res = Math.max(res,i-left+1);
        }
        return res;
    }
}
