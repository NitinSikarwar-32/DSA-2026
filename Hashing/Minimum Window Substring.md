Minimum Window Substring

Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".

The testcases will be generated such that the answer is unique.



Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.

Input: s = "a", t = "a"
Output: "a"
Explanation: The entire string s is the minimum window.


Solution:

class Solution {
    public String minWindow(String s, String t) {
        HashMap<Character,Integer>map = new HashMap<>();
        for(char ch: t.toCharArray()) {
            map.put(ch,map.getOrDefault(ch,0)+1);
        } 
        int left = 0,start=0,res=Integer.MAX_VALUE,mCount=0;
        for(int i=0;i<s.length();i++) {
            char ch = s.charAt(i);
            if(map.containsKey(ch)) {
                if(map.get(ch)>0) mCount++;
                map.put(ch,map.get(ch)-1);
            }

            while(mCount == t.length()) {
                if(i-start+1 < res) {
                    res = i-start+1;
                    left = start;
                }
                char c = s.charAt(start);
                if(map.containsKey(c)) {
                    map.put(c,map.get(c)+1);
                    if(map.get(c)>0) mCount--;
                }
                start++;
            }
        }
        return res == Integer.MAX_VALUE?"":s.substring(left,left+res);
    }
}