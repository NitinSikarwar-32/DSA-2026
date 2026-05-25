Title: Longest Consecutive Sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.



Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9

Solution:

class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer>set = new HashSet<>();
        for(int i=0;i<nums.length;i++) {
            set.add(nums[i]);
        }
        int longestStreak = 0;
        for(int num:set) {
            if(!set.contains(num-1)) {
                int currentStreak = 1;
                int currentNum = num;
                while(set.contains(currentNum+1)) {
                    currentNum++;
                    currentStreak++;
                }
                longestStreak = Math.max(longestStreak,currentStreak);
            }
        }
        return longestStreak;
    }
}
