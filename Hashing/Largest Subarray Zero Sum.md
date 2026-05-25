Title: Largest Subarray Zero Sum

Given an array arr[] of length N, find the length of the longest sub-array with a sum equal to 0.



Input: arr[] = {15, -2, 2, -8, 1, 7, 10, 23}
Output: 5
Explanation: The longest sub-array with elements summing up-to 0 is {-2, 2, -8, 1, 7}

Input: arr[] = {1, 2, 3}
Output: 0
Explanation: There is no subarray with 0 sum


Solution:

public class codefile{
    static int maxLen(int[]  input){
        int res=0,sum=0;
        Map<Integer,Integer>map=new HashMap<>();
        map.put(0,-1);
        for(int i=0;i<input.length;i++) {
          sum += input[i];
          if(map.containsKey(sum)) {
               res = Math.max(res,i-map.get(sum));
          } else {
               map.put(sum,i);
          }
        }
        return res;
    }
}