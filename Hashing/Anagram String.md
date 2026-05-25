Title: Anagram String

Check whether two Strings are anagram of each other.
Note : An anagram of a string is another string that contains the same characters, only the order of characters can be different.

Input 1: str1 = “listen” str2 = “silent”
Output 1: true
Explanation 1: All characters of “listen” and “silent” are the same.

Input 2: str1 = “gram” str2 = “arm”
Output 2: false

Solution:

public class codefile{
    static boolean check(String str1,String str2){
      if(str1.length() != str2.length()) return false;
      char[] arr1 = str1.toCharArray();
      char[] arr2 = str2.toCharArray(); 
      Arrays.sort(arr1);
      Arrays.sort(arr2);
      for(int i=0;i<arr1.length;i++) {
        if(arr1[i] != arr2[i]) {
          return false;
        }
      }
      return true;
    }
}