Daily Temperatures

Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.



Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]

Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]

Solution:
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int n = temperatures.length;
        int res[]=new int[n];
        Stack<Integer>st = new Stack<>();
        for(int i=0;i<n;i++) {
            while(!st.isEmpty() && temperatures[i]>temperatures[st.peek()]) {
                int idx = st.pop();
                res[idx] = i-idx;
            }
            st.push(i);
        }
        return res;
    }
}